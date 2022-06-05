Notes from my work through of the book zero 2 prod by Luca Palmieri.

### Faster Linking
`lld` Allows for faster compile time.
`sudo apt-get install lld clang`
in the file `.cargo/config.toml`
Recommended :
```
[target.x86_64-unknown-linux-gnu]
rustflags = ["-C", "linker=clang", "-C", "link-arg=-fuse-ld=lld"]
```
Does it work for ARM?
I'm gonna try:
```
[target.aarch64-unknown-linux-gnu]
rustflags = ["-C", "linker=clang", "-C", "link-arg=-fuse-ld=lld"]
```
... Yup, that works!
Author says to check out : mold for even faster linking.  
https://www.infoq.com/news/2021/12/mold-linker-1-0/
Article says it's leveraging multicore architecture, which should be nice on my VM. Also it's by the maker of the lld stuff.
I'm gonna check how to set it up.
... Look like it's doable. Easily
1. https://github.com/rui314/mold#compile-mold
2. https://github.com/rui314/mold#how-to-use (sub-section: If You Are Using Rust);
Trying out.
... Well, that works :o 
### Reducing "perceived" compilation time with `cargo-watch`
Looks like an equivalent to nodemon.
usage: `cargo-watch -x check`
usage avec tests: `cargo-watch -x check -x tests -x run` chain compile,puis tests, puis run.
... Yes, just tried it out, that's sweeet!
### Increasing code quality
With `let g:rustfmt_autosave = 1` in my `.vimrc` I run the formatter on save which is cool.
Right now, I'm looking for a way to run `clippy` linter before letting commits go through.
... Ok never mind, I'll do it later.

