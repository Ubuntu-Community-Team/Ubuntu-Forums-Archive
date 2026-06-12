---
title: "um, dumb question: what package is the write command in"
date: 2009-01-01
forum: Server Platforms
---

### Post by Niels Olson on 2009-01-01
turns out, it's really hard to google the answer to that question. The word "write" is just to ubiquitous in computing and the command is just so commonly installed. But SliceHost's Ubuntu builds don't come with it, and we're used to using it on our other server. Any ideas?

Feeling dumb . . .

---

### Post by amauk on 2009-01-01
bsdmainutils

installed file at /usr/bin/bsd-write

seems to be symlinked twice,
/usr/bin/write -> /etc/alternatives/write -> /usr/bin/bsd-write

---

### Post by MJN on 2009-01-02
For this sort of query, consider installing **apt-file** as, amongst other things, it allows you to find out which package installs which files.

For example,

```
$ sudo apt-file update
$ sudo apt-file search /usr/bin/write

orville-write: usr/bin/write
```(searching for 'write' alone would result on many results as it would match /usr/bin/zwrite, /usr/bin/wdwrite etc)

Hence, **orville-write** appears to be the standard Ubuntu replacement for **write **(with bsdmainutils providing an alternative as amauk said)[1].

You can take a look at the package page [here]("http://packages.ubuntu.com/intrepid/orville-write") as well as its [list of files]("http://packages.ubuntu.com/intrepid/i386/orville-write/filelist") (which confirms the native /usr/bin/write install).

Mathew

[1] Edit: It looks like orville-write was the default write replacement in Dapper. In Intrepid it appears there is no default (just alternatives). You should mention your distribution to allow specific advice.

---

