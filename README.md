# Mongo Hands On

## Start on docker

```bash
docker run --name mongo -d mongo
```

```bash
docker exec -it mongo bash
```

## Start mongo cli

Note: run this command inside mongo container.

```bash
mongosh
```

## Commands

### Create collection

```bash
db.createCollection('COLLECTION_NAME')
```

### Insert an item into a collection

```bash
db.COLLECTION_NAME.insert({ 'any_key': 'any_value' })
```

### Get all items from a collection

```bash
db.COLLECTION_NAME.find()
```

Or

```bash
db.COLLECTION_NAME.find().pretty()
```

### Remove item from a collection

```bash
db.COLLECTION_NAME.remove({
  '_id': ObjectId('ITEM_ID')
})
```

### Get items from a collection by attributes

```bash
db.COLLECTION_NAME.find({
  any_key: 'any_value'
})
```

Or

```bash
db.COLLECTION_NAME.find({
  'any_key_1.any_key_2': 'any_value'
})
```

Or

```bash
db.COLLECTION_NAME.find({
  $or: [
    { 'any_key_1.any_key_2': 'any_value_1' },
    { 'any_key_1.any_key_2': 'any_value_2' }
  ]
})
```

Or

```bash
db.COLLECTION_NAME.find({
  'any_key_1.any_key_2': {
    $in: ['any_value_1', 'any_key_2']
  }
})
```

Or

```bash
db.COLLECTION_NAME.find({
  'any_key_1.any_key_2': {
    $gt: 'any_value_1'
  }
})
```

### Get one item from a collection by attributes

```bash
db.COLLECTION_NAME.findOne({
  any_key: 'any_value'
})
```

### Get items from a collection by attributes and sort

```bash
db.COLLECTION_NAME.find({
  any_key: 'any_value'
}).sort({ any_key: 1 }) # 1 for asc and -1 for desc
```

### Get items by attributes from a collection and limit

```bash
db.COLLECTION_NAME.find({
  any_key: 'any_value'
}).limit(ANY_LIMIT)
```

### Update an item in a collection

```bash
db.COLLECTION_NAME.update(
  { any_key: 'any_value' }, # query
  { ... } # item data
)
```

Or

```bash
db.COLLECTION_NAME.update(
  { any_key: 'any_value' }, # query
  {
    $set: {
      ... # item data
    }
  } 
)
```

Or

```bash
db.COLLECTION_NAME.update(
  { any_key: 'any_value' }, # query
  {
    $set: {
      ... # item data
    }
  },
  {
    multi: true
  } 
)
```
