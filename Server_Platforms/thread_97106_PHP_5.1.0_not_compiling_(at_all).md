---
title: "PHP 5.1.0 not compiling (at all)"
date: 2005-11-30
forum: Server Platforms
---

### Post by DeusX on 2005-11-30
I have installed Apache 1.3.34 by compiling, I have installed MySQL 5.0.16 from binaries and it all came to installing PHP 5.1.0 (the latest version until this morning).

So, I have installed all libriries I needed for my ./configure script and I runned it. It was OK, but at "make", it fails to compile with strange errors about some constants not being defined and such.

A friend pointed that I may be using the wrong gcc version (which was version 4, from Ubuntu repositories). Then I have installed gcc 2.95 and 3.3 and 3.4. I have also removed (using Synaptic) gcc 4. Now I have 3 versions of gcc but I cannot compile because when I run "make", the output is "gcc: no such command found". And that's ok, since every gcc verision has it's executable file like "gcc-2.95" or "gcc-3.3".
I have tried to create an alias using "alias gcc=gcc-2.95" and it works in console, but it outputs the same error when using "make".

Please help. And please take notice that I am a newbie in Linux administration so please, be as clear as posible. :P Thanks.

---

### Post by ranf on 2005-11-30
[QUOTE=DeusX]I have installed Apache 1.3.34 by compiling, I have installed MySQL 5.0.16 from binaries and it all came to installing PHP 5.1.0 (the latest version until this morning).

So, I have installed all libriries I needed for my ./configure script and I runned it. It was OK, but at "make", it fails to compile with strange errors about some constants not being defined and such.

A friend pointed that I may be using the wrong gcc version (which was version 4, from Ubuntu repositories). Then I have installed gcc 2.95 and 3.3 and 3.4. I have also removed (using Synaptic) gcc 4. Now I have 3 versions of gcc but I cannot compile because when I run "make", the output is "gcc: no such command found". And that's ok, since every gcc verision has it's executable file like "gcc-2.95" or "gcc-3.3".
I have tried to create an alias using "alias gcc=gcc-2.95" and it works in console, but it outputs the same error when using "make".

Please help. And please take notice that I am a newbie in Linux administration so please, be as clear as posible. :P Thanks.[/QUOTE]
Alias is not the right tool for this.
Try this
```

export CC=/usr/bin/gcc-3.4

```

BTW: there is version 5.1.1 of PHP available.

---

