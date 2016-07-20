# symlinkgcc

OS X ships with `/usr/bin/gcc` not actually `gcc`, but `clang`. This will cause Makefile's relying on gcc-specific flags to fail. The `gcc` in `homebrew-core` installs to `/usr/local/bin/gcc-{major_version}`, for example `/usr/local/bin/gcc-6`. This (super) simple script symlinks `/usr/local/bin/gcc` to the latest version of `gcc`.

# Using as a formula dependency

If your formula's Makefile/compile script uses gcc-specific functionality, just add this dependency line to ensure that `gcc` is actually `gcc` and not `clang`:
```
depends_on "thepiercingarrow/homebrew-tap/symlinkgcc" => :build
```
# Installing for self use

If you are tired of typing `gcc-{version}` to use `gcc`, or changing your `.bashrc` or `.bash_profile` every time `gcc` releases a new major version, just:
```
brew install symlinkgcc
```
and `/usr/local/bin/gcc` will automatically update whenever `gcc` updates (assuming you keep `gcc` updated using `brew upgrade`).
