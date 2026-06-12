---
title: "Can anyone help me determine if there is a version of libudev shipped with ubuntu?"
date: 2013-08-05
forum: Ubuntu Application Development
---

### Post by marshzor on 2013-08-05
Hi All,

My question is simple: Can you point me to somewhere that I can find the libraries that are shipped with Ubuntu by default?

I'd like to know if libudev is shipped with Ubuntu 12.04, 12.10 and 13.04 by default.

Some background: I am building a .dpkg installer and I'd prefer to not list any specific version or range of udev libraries in my dependencies in the control.template file for my installer. I would just like to verify that my users will have udev on their ubuntu systems by default.

I have been digging through the wiki for about a half hour now and I've come up empty handed so if anyone could help it woudl be much appreciated! Please let know if you need any more information about my question, or if this is the wrong place for this thread feel free to move/remove it.

Thanks in advance!

---

### Post by ian-weisser on 2013-08-05
Here is one way to find the name of the libudev package:
```
$ apt-cache depends udev
udev
  [...]
  Depends: libudev0
  [...]
```

You are looking for "libudev0", not libudev.

Here is one way to find the versions of that package in each supported release of Ubuntu:
```
$ rmadison -u ubuntu libudev0   # rmadison is in the 'devtools' package
  libudev0 |     151-12 |         lucid | amd64, armel, i386, ia64, powerpc, sparc
  libudev0 |   151-12.3 | lucid-updates | amd64, armel, i386, ia64, powerpc, sparc
  libudev0 | 175-0ubuntu9 |       precise | amd64, armel, armhf, i386, powerpc
  libudev0 | 175-0ubuntu9.4 | precise-updates | amd64, armel, armhf, i386, powerpc
  libudev0 | 175-0ubuntu13 |       quantal | amd64, armel, armhf, i386, powerpc
```


Here is one quick way to find if a package is part of the (current) default install of Ubuntu:
```
$ apt-cache depends ubuntu-desktop | grep udev   # The Unity install of Ubuntu, including ubuntu-standard
[no result]
$ apt-cache depends ubuntu-standard | grep udev            # The command-line install of Ubuntu, including ubuntu-minimal
[no result]
$ apt-cache depends ubuntu-minimal | grep udev            # The bare-minimum bootable install of Ubuntu, missing many features
  Depends: udev

```

There are also tools in Launchpad to help determine versions and dependencies.

udev has been included in ubuntu-minimal for several years, long before 12.04.

---

### Post by Bashing-om on 2013-08-05
marshzor; Hi !
In addition.. here is the mother listing of all packages in the repositories:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Great place to start looking and drilling about.

[INDENT][INDENT]ubuntu, no secrets
[/INDENT][/INDENT]

---

### Post by marshzor on 2013-08-05
Awesome, you guys rule. This is what I needed. Thanks a lot.

---

### Post by ubuntpetbe2 on 2013-08-06
Did you find it yet?
You can add something that says it's solved.

---

### Post by marshzor on 2013-08-06
Yes sir, just added the solved tag.

---

