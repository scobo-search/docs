# Usage

---

- [Adding Object](#adding-object)
- [Searching](#searching)
- [Deleting Object](#delete-object)

<a name="adding-object"></a>
## Adding Objects
Adding an object for search is super simple and does not require any special formatting. Simply build an array with the data you want to be searchable and put it into the `addItem()` or `addItems()` function.

-----
#### Example Input
```php
$object = [
    'id' => 1,
    'title' => 'This is an Object',
    'description' => 'This is a description',
    'author' => [
        'username' => 'Matt'
    ]
];

$scoboIndex->addItem($object);
```

```php
$object = [
    [
        'id' => 1,
        'title' => 'This is an Object',
        'description' => 'This is a description',
        'author' => [
            'username' => 'Matt'
    ],
    [
        'id' => 2,
        'title' => 'This is another Object',
        'description' => 'This is another description',
        'author' => [
            'username' => 'Matt'
    ]
];

$scoboIndex->addItems($object);
```

#### Example Output
```php
'f6cfebed-412d-4237-8543-29dc0976939b'
```
> {warning} You should always store the output ID in a string value. You can only delete objects using this ID.

<a name="searching"></a>
## Searching
Searching with Scobo is just as simple as adding data to the index. There are a few available options but they are entirely optional.

----
#### Example Input
```php
$options = [
    /*
     * The search object contains data fields that should be searched.
     * If it's not included all fields will be searched.
     */
    'search' => [
        'title',
        'description'
    ],
    /*
     * The return object contains fields that should be returned.
     * If it's not included all fields will be returned.
     */
    'return' => [
        'id',
        'title',
        'description',
        'author.username'
    ]
];
$scoboIndex->search('object', $options);
```
#### Example Output
```php
[
    [
        'id' => 1,
        'title' => 'This is an Object',
        'description' => 'This is a description',
    ],
    [
        'id' => 2,
        'title' => 'This is another Object',
        'description' => 'This is a description',
    ]
]
```

<a name="delete-object"></a>
## Deleting Objects
Deleting objects is just as easy as adding them.

----
> {warning} The ID used for removal must be the one returned from the `add()` function.

#### Example Input
```php
$scoboIndex->remove('f6cfebed-412d-4237-8543-29dc0976939b');
```
