# Rust Mastery Roadmap (Beginner-Friendly)

You can use this as a checklist. It’s designed for someone with no C/Rust background and should lead to a **solid** understanding of how Rust works and how to use it. Each step includes a specific practice objective and expected result to ensure you retain what you learn.

---

## Phase 0 – Setup and Mindset

- **Install Rust** using `rustup` (includes `rustc`, `cargo`, `rustup`).
- **Install an editor** with Rust support (VS Code + Rust Analyzer, IntelliJ Rust, or CLion).
- **Set up Git** and create a GitHub account for version control.
- **Skim the introduction** and “How to Use This Book” section of *The Rust Programming Language* (“The Book”).
- **Mindset shift:** Accept that Rust feels strict at first; the compiler is your guide, not your enemy.

**Practice:** Run `cargo --version` and `rustc --version` in your terminal.
- *Objective:* Confirm your toolchain is working.
- *Result:* The terminal outputs the current versions of Cargo and the Rust compiler.

---

## Phase 1 – First Contact with Rust

1. **Hello World and Tooling**
   - Create a new project with `cargo new hello_rust`.
   - Understand `Cargo.toml`, `src/main.rs`, `cargo build`, `cargo run`, `cargo check`.
   - **Practice:** Modify the `main.rs` file to print "Hello, [Your Name]!" and use `cargo run`.
     - *Objective:* Learn the basic Cargo workflow.
     - *Result:* The program compiles without errors and prints your custom message to the console.

2. **Basic Syntax**
   - Learn `fn main()`, `let` bindings, `mut`, comments, and basic formatting with `println!`.
   - Practice with integers, floats, booleans, chars, and tuples in small programs.
   - **Practice:** Write a simple temperature converter that takes a hardcoded Celsius float, converts it to Fahrenheit, and prints it using a tuple `(celsius, fahrenheit)`.
     - *Objective:* Understand basic scalar types, math operations, and `println!` formatting.
     - *Result:* A program that correctly calculates and prints `25.0C is 77.0F`.

3. **Control Flow**
   - Practice `if`, `else if`, `else` with multiple conditions.
   - Use `loop`, `while`, and `for` loops to iterate numbers and collections.
   - **Practice:** Implement the classic "FizzBuzz" problem. Use a `for` loop from 1 to 100. If divisible by 3, print "Fizz"; by 5, print "Buzz"; by both, print "FizzBuzz"; otherwise, print the number.
     - *Objective:* Master `for` loops, `if/else if/else` logic, and the modulo (`%`) operator.
     - *Result:* Your terminal outputs the correct sequence from 1 to 100 with the appropriate word replacements.

---

## Phase 2 – Core Rust Concepts

4. **Variables, Shadowing, and Types**
   - Understand immutability by default and when to use `mut`.
   - Practice “shadowing” (reusing variable names with `let`) and see how types are inferred.
   - **Practice:** Write a program that takes a string of spaces (e.g., `let spaces = "   ";`), and uses shadowing to replace it with the number of spaces (`let spaces = spaces.len();`).
     - *Objective:* Prove that shadowing allows changing a variable's type, which `mut` does not allow.
     - *Result:* Code compiles successfully, demonstrating type transformation without needing a new variable name.

5. **Functions and Expressions**
   - Define functions with parameters and return values.
   - Learn that blocks `{}` are expressions that produce values if they don't end in a semicolon.
   - **Practice:** Write an `fn calculate_area(width: u32, height: u32) -> u32` function. Call it inside an `if let` or a `println!` block.
     - *Objective:* Learn how to pass arguments and return values implicitly (without the `return` keyword).
     - *Result:* The program accurately outputs the area calculation.

6. **Ownership – The Heart of Rust**
   - Learn the three ownership rules: each value has one owner, moves, and drops when the owner goes out of scope.
   - **Practice:** Create two strings, `s1` and `s2`. Assign `s1` to `s2`. Try to print `s1`. Read the compiler error, then fix it by using `.clone()`.
     - *Objective:* Physically encounter and resolve a "use of moved value" compiler error.
     - *Result:* You understand the difference between moving data and cloning heap data.

7. **Borrowing and References**
   - Understand `&T` (immutable reference) and `&mut T` (mutable reference).
   - Learn the rule: You can have *either* one mutable reference *or* multiple immutable references.
   - **Practice:** Write an `fn add_exclamation(s: &mut String)` that pushes a `!` to the end of a string. Call it from main without transferring ownership.
     - *Objective:* Modify data without taking ownership of it.
     - *Result:* The string is modified in place, and you can still print it in `main` afterward.

8. **Slices and Strings**
   - Learn string slices `&str` vs owned `String`.
   - **Practice:** Write an `fn first_word(s: &str) -> &str` that finds the first space in a string and returns a slice of the word before it.
     - *Objective:* Learn to reference a contiguous sequence of elements in a collection rather than the whole collection.
     - *Result:* You can extract and print the first word of a sentence without copying the underlying string data.

---

## Phase 3 – Data Structures and Abstraction

9. **Structs**
   - Define simple `structs` with named fields.
   - Implement `impl` blocks with methods (`&self`) and associated functions (`Self::new`).
   - **Practice:** Create a `Rectangle` struct with `width` and `height`. Write an `impl` block with an `area(&self) -> u32` method and a `square(size: u32) -> Rectangle` associated function.
     - *Objective:* Group related data together and tie functions directly to that data.
     - *Result:* You can instantiate a rectangle and call `rect.area()` using method syntax.

10. **Enums and Pattern Matching**
    - Learn enums with variants and `match` expressions.
    - **Practice:** Create an `enum TrafficLight { Red, Yellow, Green }`. Write a `match` statement that prints a specific instruction (Stop, Slow, Go) for each variant.
      - *Objective:* Ensure exhaustive checking (the compiler forces you to handle every enum variant).
      - *Result:* The compiler prevents you from missing a traffic light state, proving Rust's safety.

11. **Collections**
    - Explore `Vec<T>`, `String`, and `HashMap<K, V>` from the standard library.
    - **Practice:** Given a list of integers (`Vec<i32>`), write code to find the mean (average), median (middle value after sorting), and mode (value that occurs most often using a `HashMap`).
      - *Objective:* Become comfortable mutating vectors and inserting data into HashMaps.
      - *Result:* The program outputs correct statistical values for any given array of numbers.

12. **Error Handling**
    - Learn idiomatic error handling with `Result<T, E>`, the `?` operator, and `Option<T>`.
    - **Practice:** Write a function that reads a username from a file (`fn read_username() -> Result<String, io::Error>`). Use the `?` operator to propagate errors if the file doesn't exist.
      - *Objective:* Move away from using `.unwrap()` or `.expect()` and gracefully handle failures.
      - *Result:* If the file is missing, the program doesn't crash (panic); it safely returns the error to `main` to be printed.

---

## Phase 4 – Generic Code and Traits

13. **Generics**
    - Learn basic generics on functions, structs, and enums.
    - **Practice:** Write an `fn largest<T>(list: &[T]) -> &T` that returns the largest item in a slice. (You will need to use traits like `PartialOrd` to make it compile).
      - *Objective:* Write one function that works for both `Vec<i32>` and `Vec<char>`.
      - *Result:* Code deduplication; you use the same logic for multiple data types.

14. **Traits**
    - Understand traits as shared behavior (similar to interfaces in other languages).
    - **Practice:** Define a `Summary` trait with a `summarize(&self) -> String` method. Implement it for two different structs (e.g., `NewsArticle` and `Tweet`).
      - *Objective:* Define polymorphism in Rust.
      - *Result:* You can write a function that accepts `item: &impl Summary` and prints the summary, regardless of whether it's an article or a tweet.

15. **Lifetimes (Practical Level)**
    - Learn when the compiler asks for explicit lifetimes (`'a`).
    - **Practice:** Write a function that takes two string slices and returns the longest one. Attempt it without lifetimes to see the error, then add `<'a>` to fix it (`fn longest<'a>(x: &'a str, y: &'a str) -> &'a str`).
      - *Objective:* Tell the compiler how the lifespans of references relate to each other so it can prevent dangling pointers.
      - *Result:* Code compiles, and you understand that lifetimes don't change how long data lives, they just describe it to the borrow checker.

---

## Phase 5 – The Rust Ecosystem and Projects

16. **Cargo and Crates.io**
    - Explore `cargo` commands and external dependencies.
    - **Practice:** Add the `rand` crate to your `Cargo.toml`. Generate a random number between 1 and 100 and print it.
      - *Objective:* Learn how to use third-party libraries.
      - *Result:* Your program compiles with downloaded dependencies and outputs a random number.

17. **Testing and Documentation**
    - Write unit tests with `#[test]` and use doc comments `///`.
    - **Practice:** Create a simple math module. Write `///` comments explaining the functions, then write `#[test]` modules at the bottom of the file to test math logic. Run `cargo test` and `cargo doc --open`.
      - *Objective:* Build habits for Test-Driven Development (TDD) and documentation.
      - *Result:* Tests pass in the terminal, and a browser opens displaying beautifully formatted HTML documentation for your code.

18. **Command-Line Application (Milestone Project)**
    - Build a realistic CLI tool.
    - **Practice:** Build "Mini-Grep", a program that takes a search string and a filename as arguments, reads the file, and prints lines containing the search string. Use the `env::args` iterator.
      - *Objective:* Combine structs, error handling, traits, and file I/O into a real application.
      - *Result:* A functional CLI tool you can run via `cargo run -- "search_term" text.txt` that behaves like a basic Unix tool.

---

## Phase 6 – Memory, Concurrency, and Async

19. **Smart Pointers**
    - Learn about `Box<T>`, `Rc<T>`, and `Arc<T>`.
    - **Practice:** Use `Box<T>` to create a recursive Cons list (a linked list: `enum List { Cons(i32, Box<List>), Nil }`).
      - *Objective:* Allocate data on the heap when you have types of unknown size at compile time.
      - *Result:* You successfully bypass the compiler error regarding "infinite size" structs/enums.

20. **Interior Mutability**
    - Explore `RefCell<T>` and `Mutex<T>` for controlled mutation.
    - **Practice:** Combine `Rc<T>` and `RefCell<T>` to create a struct that can have multiple owners, but whose inner data can still be mutated (`Rc<RefCell<i32>>`).
      - *Objective:* Bypass strict compile-time borrowing rules by enforcing them at runtime.
      - *Result:* You can modify a value through multiple different shared references safely.

21. **Concurrency**
    - Learn Rust’s threads, channels, and message passing.
    - **Practice:** Spawn 5 threads using `thread::spawn`. Have each thread send a specific message back to the main thread via a channel (`mpsc::channel`). Receive and print them in main.
      - *Objective:* Experience "fearless concurrency" and safely pass data between threads.
      - *Result:* Output prints messages from 5 different threads in non-deterministic order without race conditions.

22. **Asynchronous Programming**
    - Study `async`/`await`, and executors (like `tokio`).
    - **Practice:** Add `tokio` and `reqwest` to `Cargo.toml`. Write an `async fn` that makes an HTTP GET request to a public API (like JSONPlaceholder) and prints the status code.
      - *Objective:* Understand how Rust handles non-blocking I/O tasks.
      - *Result:* Your program successfully fetches web data asynchronously using the `.await` syntax.

---

## Phase 7 – Advanced Topics and Specialization

23. **Macros**
    - Learn the difference between declarative macros (`macro_rules!`) and procedural macros.
    - **Practice:** Write a simple `macro_rules!` called `my_vec!` that initializes a vector with given elements, mimicking the standard `vec!` macro.
      - *Objective:* Understand metaprogramming (code that writes code).
      - *Result:* You can initialize a vector by writing `let v = my_vec![1, 2, 3];`.

24. **Specialization Project**
    - Choose a domain to dive deep into.
    - **Practice:** Based on your interest, build one of the following:
      - *Web Backend:* Build a simple REST API using `Axum` or `Actix` with a database connection.
      - *Systems:* Build a simple chip-8 emulator or a custom CLI task manager.
      - *Objective:* Transition from "learning Rust" to "using Rust".
      - *Result:* A portfolio-ready project demonstrating your competence in a specific ecosystem.

---

## Suggested Order and Time Estimate

You can treat these as flexible “weeks” depending on your schedule.

- Weeks 1–2: Phases 1–2 (syntax, ownership, borrowing).
- Weeks 3–5: Phases 3–4 (data structures, traits, generics).
- Weeks 6–8: Phase 5 (CLI project, tests, docs).
- Weeks 9–12: Phases 6–7 (concurrency, async, specialization project).
- Ongoing: Phase 8 (practice, reading, community, projects).

