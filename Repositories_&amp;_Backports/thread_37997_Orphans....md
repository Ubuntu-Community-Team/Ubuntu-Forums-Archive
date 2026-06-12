---
title: "Orphans..."
date: 2005-05-29
forum: Repositories &amp; Backports
---

### Post by Vrok on 2005-05-29
*(I hope I've chosen correct forum)*

I recently installed deborphan package from Universe, and it says that only one library in my system is orphaned - libarr0. But, I think it should return at least two libraries - iso-codes and libarr0 - both of them are in my system and both don't have any reverse dependecies installed. Maybe any of you know what's the cause of it.

Here's some info about those packages:

Package: iso-codes
Priority: optional
Section: libs
Installed-Size: 4548
Maintainer: Alastair McKinstry <mckinstry@debian.org>
Architecture: all
Version: 0.45-1ubuntu1
Filename: pool/main/i/iso-codes/iso-codes_0.45-1ubuntu1_all.deb
Size: 1055758
MD5Sum: 6203d07e2ea632ae37eba7a6b53c6fa0
Description: ISO language, territory, currency  codes and their translations
 This package provides the ISO-639 Language code list, the
 ISO-4217 currency list, the ISO-3166 Territory code list,
 and ISO-3166-2 sub-territory lists.
 .
 It also (more importantly) provides their translations in .po form.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-ship

Package: libarr0
Priority: optional
Section: universe/libs
Installed-Size: 72
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: i386
Source: libarr
Version: 0.1-52
Depends: libc6 (>= 2.3.2.ds1-4)
Filename: pool/universe/liba/libarr/libarr0_0.1-52_i386.deb
Size: 18088
MD5sum: 410d7990d5c137677edbf16183979f81
Description: a small, fast console drawing library
 libarr is a small and fast console management library.
 it was intended to replace the drawing functionality of
 SLang as used in libctk.  It stores up writes, and then
 does them all at once by only writing the difference
 to the screen.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by jobezone on 2005-05-29
[QUOTE=Vrok]*(I hope I've chosen correct forum)*

I recently installed deborphan package from Universe, and it says that only one library in my system is orphaned - libarr0. But, I think it should return at least two libraries - iso-codes and libarr0 - both of them are in my system and both don't have any reverse dependecies installed. Maybe any of you know what's the cause of it.

Here's some info about those packages:

Package: iso-codes
Priority: optional
Section: libs
Installed-Size: 4548
Maintainer: Alastair McKinstry <mckinstry@debian.org>
Architecture: all
Version: 0.45-1ubuntu1
Filename: pool/main/i/iso-codes/iso-codes_0.45-1ubuntu1_all.deb
Size: 1055758
MD5Sum: 6203d07e2ea632ae37eba7a6b53c6fa0
Description: ISO language, territory, currency  codes and their translations
 This package provides the ISO-639 Language code list, the
 ISO-4217 currency list, the ISO-3166 Territory code list,
 and ISO-3166-2 sub-territory lists.
 .
 It also (more importantly) provides their translations in .po form.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-ship

Package: libarr0
Priority: optional
Section: universe/libs
Installed-Size: 72
Maintainer: Debian QA Group <packages@qa.debian.org>
Architecture: i386
Source: libarr
Version: 0.1-52
Depends: libc6 (>= 2.3.2.ds1-4)
Filename: pool/universe/liba/libarr/libarr0_0.1-52_i386.deb
Size: 18088
MD5sum: 410d7990d5c137677edbf16183979f81
Description: a small, fast console drawing library
 libarr is a small and fast console management library.
 it was intended to replace the drawing functionality of
 SLang as used in libctk.  It stores up writes, and then
 does them all at once by only writing the difference
 to the screen.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu[/QUOTE]
 you could try removing them, and see if they want to remove another package? If not, and everything works fine, then they weren't needed by you.

the deborphan package has many options to fine-tune which types of orphaned packages he spits out, but I don't use it beside the simplest way, running just deborphan. Run "man deborphan" and see inside the /usr/share/doc/deborphan/ directory for more options.

---

### Post by Vrok on 2005-05-31
[QUOTE=jobezone]you could try removing them, and see if they want to remove another package? If not, and everything works fine, then they weren't needed by you.
[/quote]
Yeah, it works. But I think I know why it happened...

vrok@ankh ~ $ apt-cache show iso-codes | grep ^Section
Section: libs
vrok@ankh ~ $ dpkg -p iso-codes | grep ^Section
Section: misc

It's either a bug or my lack of knowlegde.

---

### Post by jobezone on 2005-05-31
[QUOTE=Vrok]Yeah, it works. But I think I know why it happened...

vrok@ankh ~ $ apt-cache show iso-codes | grep ^Section
Section: libs
vrok@ankh ~ $ dpkg -p iso-codes | grep ^Section
Section: misc

It's either a bug or my lack of knowlegde.[/QUOTE]
 What if you had tried ```
deborphan --guess-all
```?

The man page for deborphan tells about --guess-all:
> 
--guess-*
              deborphan can try to guess what packages may not be of much  use
              to  you  by  examining the package’s name and/or description. It
              will pretend the package is in the main/libs section, and report
              it  as if it were a library. This method is in no way perfect or
              even reliable, so beware when using this!
[...] all    Try all of the above.

---

