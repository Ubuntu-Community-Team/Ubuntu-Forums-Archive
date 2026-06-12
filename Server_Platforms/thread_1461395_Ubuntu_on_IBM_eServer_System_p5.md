---
title: "Ubuntu on IBM eServer System p5"
date: 2010-04-24
forum: Server Platforms
---

### Post by greenmang0 on 2010-04-24
hello friends,
I am trying to install Ubuntu Server Edition ([http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/karmic/release/ubuntu-9.10-alternate-powerpc.iso)) on IBM eServer System p5.

I get a boot prompt where I enter
"expert install video=ofonly"

It loads kernel then ELF and then I get a screen saying,


done
instantiating rtas at 0x07716000 .... done
WARNING: maximum cups (1) exceeded:  ignoring extras
copying OF device tree...
Building dt strings...
Building dt structure....
Device tree strings 0x01e01000 -> 0x01d023b3
Device tree struct 0x01e03000 -> 0x01e12000
Calling quiesce....
returning from prom_init
_


and the system freezes.

What can be the solution? for this problem?

---

### Post by scprotz on 2010-12-07
Same problem on Intellistation Power 185 (PPC970MP CPUs).

I did get Fedora 12 to install.  Any luck with Ubuntu?

---

