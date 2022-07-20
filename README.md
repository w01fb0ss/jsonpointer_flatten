# jsonpointer_flatten

[![crates.io](https://img.shields.io/crates/v/jsonpointer_flatten.svg)](https://crates.io/crates/jsonpointer_flatten)
[![docs.rs](https://docs.rs/jsonpointer_flatten/badge.svg)](https://docs.rs/jsonpointer_flatten/0.1.3/jsonpointer_flatten/)

Rust library to flatten a JSON object using JSON Pointer field addressing as defined in [IETF RFC 6901](https://datatracker.ietf.org/doc/html/rfc6901).

## Usage

```rust
let value = json!(
    {
        "name": "John Smith",
        "age": 24,
        "address": {
            "country": "US",
            "zip": "00000"
        },
        "phones": [ "123", "456" ]
    }
);

let actual = jsonpointer_flatten::from_json(&value);
```

Outputs
```json
{
  "root.address.country": "US",
  "root.address.zip": "00000",
  "root.age": 24,
  "root.name": "John Smith",
  "root.phones.0": "123",
  "root.phones.1": "456"
}
```