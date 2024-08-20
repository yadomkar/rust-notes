
# Rust Strings

Rust provides two main types of strings: `String` and `&str`.

## `&str`
- `&str` is a string slice and is the most primitive string type.
- It is typically viewed as a reference to some UTF-8 data.
- Immutable and usually points to a fixed-sized string somewhere in memory.

### Example Usage of `&str`
```rust
let greeting: &str = "Hello, world!";
println!("{}", greeting);
```

## `String`
- `String` is a growable, mutable, owned, UTF-8 encoded string type.
- It's allocated on the heap and can be modified, resized, or appended to.

### Creating a `String`
- `String::from` is used to create a `String` from a string literal.

#### Why use `String::from`?
- `String::from` is used to convert a string literal (which is of type `&str`) into a `String`. This is necessary for cases where mutability or ownership is required, such as modifying the string or transferring it across different parts of a program.

### Example Usage of `String::from`
```rust
let mut s = String::from("Hello");
s.push_str(", world!");
println!("{}", s);
```

## Operations on Strings

### Appending to a String
- You can append to a `String` using `push_str` to add a slice, or `push` to add a single character.

```rust
let mut s = String::from("foo");
s.push_str("bar");
s.push('!');
println!("{}", s); // Outputs: foobar!
```

### Concatenation
- Rust does not support using `+` directly on two `String` objects. However, you can use `+` if one of the operands is `&str`.

```rust
let s1 = String::from("Hello");
let s2 = " world!";
let s3 = s1 + s2; // Note: s1 is moved here and can no longer be used
println!("{}", s3);
```

### Indexing
- Rust strings cannot be indexed by integer positions due to UTF-8 encoding.

```rust
let s = String::from("hello");
// let h = s[0]; // This line will cause a compile-time error!
```

### Slicing
- You can get slices of strings, but you need to be careful with UTF-8 boundaries.

```rust
let s = String::from("नमस्ते");
let s_slice = &s[0..6]; // Correct: Each Unicode character (Devanagari) here takes 3 bytes
println!("{}", s_slice); // Outputs: नम
```

### Conversion between `String` and `&str`
- You can easily convert a `String` to a `&str` by taking a reference:

```rust
let s = String::from("example");
let slice: &str = &s;
```

- Conversely, you can create a `String` from a `&str` using `String::from()`.

```rust
let slice = "example";
let s = String::from(slice);
```

## Conclusion
- Use `&str` for fixed-size, immutable text data.
- Use `String` when you need a modifiable, owned string.
- Conversions and operations like appending, slicing, and concatenating are fundamental for managing strings in Rust.

