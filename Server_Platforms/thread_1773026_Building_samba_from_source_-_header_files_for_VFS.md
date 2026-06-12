---
title: "Building samba from source - header files for VFS"
date: 2011-06-01
forum: Server Platforms
---

### Post by wall_e on 2011-06-01
Hello guys.

I am quite new to installing software from source.

I have installed samba from source using ./configure + make + make install - in this order.

Everything seems to have gone ok - no errors.

However I need to find the header files in order to compile a particular VFS that I want to use.

The problem is I cannot find these in the location I thought they would be in.

The VFS that I am using needs to be built using header files that should put into/usr/src/packages/BUILD/samba-*version* during the make process of building samba.

I'm confused.

I've searched the system, but can't find them anywhere.

Any ideas. The VFS I want to use is here
[http://ingex.sourceforge.net/MediaHarmony/](http://ingex.sourceforge.net/MediaHarmony/)

The instructions are for SUSE, but I'm sure it can be done with Ubuntu too.

Any ideas? Thanks.

---

### Post by wall_e on 2011-06-02
Any ideas guys?

---

### Post by cracker89 on 2011-06-02
What version of Samba?

---

### Post by wall_e on 2011-06-03
Sorry I should have said in the original post.

Samba Version is 3.5.8 on Ubuntu Desktop 11.04

I built this from the source available on the samba site.

I just unpacked, ./configure + make + make install.

Funny thing is these files are created when I install on SUSE, but Ubuntu is my preferred distro.

---

### Post by wall_e on 2011-06-03
Update.

Well unless anybody can tell me otherwise it seems that getting the samba headers on debian isn't as straight forward as one might hope.

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg754855.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg754855.html)

It can probably be done, but in my case this might mean switching distro's :(

---

