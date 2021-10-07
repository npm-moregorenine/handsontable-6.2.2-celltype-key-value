# handsontable-6.2.2-celltype-key-value

[![](https://img.shields.io/npm/v/handsontable-6.2.2-celltype-key-value.svg?style=flat)](https://www.npmjs.com/package/handsontable-6.2.2-celltype-key-value)

Handsontable(version 6.2.2) plugin allowing to have a key-value pair as a data type. It's built upon the builtin `autocomplete` feature with some small tweaks to make it work with such use-case.

## [Demo](https://stackblitz.com/edit/handsontable-key-value-demo)

## Installation

```bash
npm i handsontable-6.2.2-celltype-key-value
```

## Usage

Use it as a column type and provide the required settings:

```js
import 'handsontable-6.2.2-celltype-key-value' // Import the module to register the extensions

const settings = {
  columns: [
    {
      type: 'key-value',
      data: 'status', // The field containing the key value in your data
      // List of source items
      source: [
        {
          id: 1,
          name: 'Ready',
        },
        {
          id: 2,
          name: 'Cancelled',
        },
        {
          id: 3,
          name: 'Done',
        },
      ],
      keyProperty: 'id', // The field containing the key value in your items
      valueProperty: 'name', // The field containing the display value in your items
    },
  ],
};
```

The `source` parameter also accepts a function for loading items asynchronously:

```js
const settings = {
  columns: [
    {
      type: 'key-value',
      data: 'status',
      source: function(_query, process) {
        const r = [
          {
            id: 1,
            name: 'Ready',
          },
          {
            id: 2,
            name: 'Cancelled',
          },
          {
            id: 3,
            name: 'Done',
          },
        ];
        setTimeout(() => process(r), 1000); // Call the `process` callback with your items.
      },
      keyProperty: 'id',
      valueProperty: 'name',
    },
  ],
};
```

## Limitations
- The sort is done on the **underlying value**, not the displayed one (unless you provide a custom compare function).

## Reference
- <https://www.npmjs.com/package/handsontable-key-value>
