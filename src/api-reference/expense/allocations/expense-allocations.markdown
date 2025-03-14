---
title: Allocations
layout: reference
---

# Allocations v3

The SAP Concur Allocations API allows for the retrieval of allocation information as it relates to a Report ID, Entry ID, or Itemization ID. Using this API allows for an in-depth review of Expense Report Data and how that data has been allocated in SAP Concur. The Allocations API allows for the programmatic gathering of details on how the expense report data was allocated by the report owner, making it ideal for Data Gathering, Expense Reporting, and Validations.

## Retrieve All Allocations Per Entry or Report <a name="get"></a>

    GET  /api/v3.0/expense/allocations

### Parameters

|Name | Type | Format | Description|
|-----|------|--------|------------|
|`limit`|`Int32`|`query`|The number of records to return. The default is 25 and the maximum is 100.
|`offset`|`string`|`query`|The starting point of the next set of results, after the limit specified in the limit field has been reached.
|`reportID`|`string`|`query`|The unique identifier for the report as it appears in the Concur Expense UI. Format: A variable-length string. Maximum length: 32 characters.
|`entryID`|`string`|`query`|The unique identifier for the expense entry.
|`itemizationID`|`string`|`query`|The unique identifier for the expense itemization.

Note: userId is not a supported query string parameter for this API.

### Request URL

```
https://www.concursolutions.com/api/v3.0/expense/allocations?limit=10
```


### JSON Example of a Successful Response

```json
{
  "Items": [
    {
      "EntryID": "gWidFO7ikXSy7gHnNngC12jkL7khMiREv4g",
      "Percentage": "100.00000000",
      "IsPercentEdited": false,
      "IsHidden": true,
      "AccountCode1": "1",
      "AccountCode2": null,
      "Custom1": null,
      "Custom2": null,
      "Custom3": null,
      "Custom4": null,
      "Custom5": null,
      "Custom6": null,
      "Custom7": null,
      "Custom8": null,
      "Custom9": null,
      "Custom10": null,
      "Custom11": null,
      "Custom12": null,
      "Custom13": null,
      "Custom14": null,
      "Custom15": null,
      "Custom16": null,
      "Custom17": null,
      "Custom18": null,
      "Custom19": null,
      "Custom20": null,
      "ID": "gWmudeHM8AuFikny3Hrpz$s2gaNvc0E7Xfyw",
      "URI": "https://www.concursolutions.com/api/v3.0/expense/allocations/gWmudeHM8AuFikny3Hrpz$s2gaNvc0E7Xfyw"
    },
    {
      "EntryID": "gWidFO7ikXSy41$smPkwdC5cL1aku$pSgc$p4g",
      "Percentage": "100.00000000",
      "IsPercentEdited": false,
      "IsHidden": true,
      "AccountCode1": "1",
      "AccountCode2": null,
      "Custom1": null,
      "Custom2": null,
      "Custom3": null,
      "Custom4": null,
      "Custom5": null,
      "Custom6": null,
      "Custom7": null,
      "Custom8": null,
      "Custom9": null,
      "Custom10": null,
      "Custom11": null,
      "Custom12": null,
      "Custom13": null,
      "Custom14": null,
      "Custom15": null,
      "Custom16": null,
      "Custom17": null,
      "Custom18": null,
      "Custom19": null,
      "Custom20": null,
      "ID": "gWmudeHM8AuFhxez1E72ExJPksvTH0KPPyw",
      "URI": "https://www.concursolutions.com/api/v3.0/expense/allocations/gWmudeHM8AuFhxez1E72ExJPksvTH0KPPyw"
    }
  ]
}
```

### Response

[Allocations Schema](#schema)


## Retrieve a Single Allocation by ID <a name="getID"></a>

    GET  /api/v3.0/expense/allocations/{id}


### Parameters

|Name | Type | Format | Description|
|-----|------|--------|------------|
|`id`|`string`|`path`|**Required** The unique identifier for the allocation.
|`user`|`string`|`query`|The login ID of the user who owns the allocation. The user must have the Web Services Admin role to use this parameter.|



## Schema <a name="schema"></a>

### <a name="allocations"></a>Allocations

|Name | Type | Format | Description|
|-----|------|--------|------------|
|`Items`|`array`|[`Allocation`](#allocations)|The result collection.
|`NextPage`|`string`|-|The URI of the next page of results, if any.|

### <a name="allocation"></a>Allocation

|Name | Type | Format | Description|
|-----|------|--------|------------ |
|`AccountNumber`|`string`|-|The primary accounting code assigned to the expense type associated with this allocation. Typically, expense types have only a primary account code.
|`AccountCode2`|`string`|-|The secondary or alternative accounting code assigned to the expense type associated with this allocation.
|`Custom1 through Custom20`|`CustomFieldExtension`|-|A custom field associated with the allocation. This field may or may not have data, depending on how Expense is configured. Format: Text field. Maximum length: 64 characters.
|`EntryID`|`string`|-|The unique identifier for the expense entry.
|`ID`|`string`|-|The unique identifier of the resource.
|`IsHidden`|`Boolean`|-|Indicates whether the allocation is hidden. Format: true or false
|`IsPercentEdited`|`Boolean`|-|Indicates whether the percentage has been edited. Format: true or false
|`Percentage`|`string`|-|The percentage of the expense that is included in this allocation.
|`URI`|`string`|-|The URI to the resource.|

### <a name="status"></a>Custom Field

|Name | Type | Format | Description|
|-----|------|--------|------------|
|`Code`|`string`|-|For list fields, this is the list item code.
|`Label`|`string`|-|The label value for the custom field.
|`ListItemID`|`string`|-|For list fields, this is the list item ID.
|`Sequence`|`integer`|-|The sequence value for this custom field i.e. the order in which this field appears on the form.
|`Type`|`string`|-|The custom field type. Possible values: Amount, Boolean, ConnectedList, Date, Integer, List, Number, Text
|`Value`|`string`|-|The value in the Org Unit or Custom field. For list fields, this is the name of the list item. Maximum length: 48 characters|

### Request URL

```
https://www.concursolutions.com/api/v3.0/expense/allocations/gWmudeHM8AuFlD9Py%24p7cwkclNQvGC1JQPyw
```


### JSON Example of a Successful Response

```json
{
  "EntryID": "gWidFO7ikXSy8HdaIfw32sJhcmk76TjD$p4g",
  "Percentage": "100.00000000",
  "IsPercentEdited": false,
  "IsHidden": true,
  "AccountCode1": "1",
  "AccountCode2": null,
  "Custom1": null,
  "Custom2": null,
  "Custom3": null,
  "Custom4": null,
  "Custom5": null,
  "Custom6": null,
  "Custom7": null,
  "Custom8": null,
  "Custom9": null,
  "Custom10": null,
  "Custom11": null,
  "Custom12": null,
  "Custom13": null,
  "Custom14": null,
  "Custom15": null,
  "Custom16": null,
  "Custom17": null,
  "Custom18": null,
  "Custom19": null,
  "Custom20": null,
  "ID": "gWmudeHM8AuFlD9Py$p7cwkclNQvGC1JQPyw",
  "URI": "https://www.concursolutions.com/api/v3.0/expense/allocations/gWmudeHM8AuFlD9Py$p7cwkclNQvGC1JQPyw"
}
```
