
ULua: Universal Lua Distribution
================================

A Lua distribution for Windows, OSX and Linux based on LuaJIT:

| OS      | Architecture | Version                                   |
|---------|--------------|-------------------------------------------|
| Windows | x86/x64      | from Windows 7 onward                     |
| OSX     | x86/x64      | from 10.5 (Leopard) onward                |
| Linux   | x86/x64      | all common distributions from 2009 onward |

## Features

- binary distribution: no need for a C/C++ compiler, adding new packages is quick and painless
- portable: it's self-contained in a single folder which can be safely relocated, even to a different OS
- no installer is needed and all required dynamic libraries are included
- includes a package manager to install new packages and to keep ULua up to date (LuaJIT binaries and package manager itself included)

## Install

Download and unzip [ulua~latest.zip](http://ulua.io/download/ulua~latest.zip) into an arbitrary folder. This will create a single sub-folder named `ulua` which contains the ULua distribution.

```
ulua
├── lua.cmd        # LuaJIT executable for Windows.
├── lua            # LuaJIT executable for OSX and Linux.
├── host
│   ├── config.lua # Global configuration (see PKG).
│   ├── init       # Initialization scripts folder.
│   ├── tmp        # Temporary files folder.
│   └── pkg        # Downloaded packages cache folder.
├── bin
│   ├── upkg.cmd   # Package manager executable for Windows.
│   ├── upkg       # Package manager executable for OSX and Linux.
│   └── ...        # Other executables depending on installed packages.
├── pkg            # Package manager package.
└── ...            # Other installed packages.
```

## Run

The `lua` executable starts LuaJIT, the [Lua manual](http://www.lua.org/manual/5.1/manual.html#6) and the [LuaJIT manual](http://luajit.org/running.html) document its usage:

```
# On Windows:
> cd folder_containing_ulua/ulua
> lua      [options] [script [args]]

# On OSX and Linux:
> cd folder_containing_ulua/ulua
> ./lua    [options] [script [args]]
```

By default LuaJIT runs in 32-bit mode, to run it in 64-bit mode set the environment variable `BIT=64`:

```
# On Windows:
> set BIT=64

# On OSX and Linux:
> export BIT=64
```

On Linux, if LuaJIT 32-bit is executed on a distribution lacking the 32-bit C runtime, this will result in a meaningless error such as `luajit: command not found`. Either launch LuaJIT in 64-bit mode or install the required Linux libraries.

## Packages

The `upkg` executable provides a convenient way of managing ULua:

```
# On Windows:
> cd folder_containing_ulua/ulua/bin
> upkg available    # List all available packages.
> upkg add socket   # Download and install the socket package (LuaSocket library).
> upkg add pl       # Download and install the pl package (PenLight library).
> upkg update       # Update all packages to the latest version.

# On OSX and Linux:
> cd folder_containing_ulua/ulua/bin
> ./upkg available  # List all available packages.
> ./upkg add socket # Download and install the socket package (LuaSocket library).
> ./upkg add pl     # Download and install the pl package (PenLight library).
> ./upkg update     # Update all packages to the latest version.
```

## Luarocks

ULua features [LuaRocks](https://luarocks.org/) integration: new and updated rocks are automatically tracked, compiled and made available in ULua. More than 300 of such packages are currently available for installation.

## Documentation

Refer to the [official documentation](http://ulua.io).
