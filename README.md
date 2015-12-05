## pkg-config for premake

This module contains a pure lua implementation of the pkg-config utility that
can be used in premake projects to query information about installed libraries.

To use it, simply install this module somewhere premake can find it. One way is
to add it as a submodule of your premake project:

```
git submodule add https://github.com/tarruda/premake-pkgconfig pkgconfig
```

Then use pkgconfig.load to return a table with data about installed libraries:

```lua
local pkgconfig = require 'pkgconfig'
print(pkgconfig.load('zlib').cflags)
print(pkgconfig.load('glib-2.0').libs)
```

The `load` function will look for .pc files in a set of predefined search
paths(see `man pkg-config`). Extra search paths can be provided either as the
second argument or through the `PKG_CONFIG_PATH` environment variable:

```lua
pkgconfig.load('mylib', {'/opt/pkgconfig', '/home/user/pkgconfig'})
```
