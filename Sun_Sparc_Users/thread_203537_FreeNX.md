---
title: "FreeNX"
date: 2006-06-25
forum: Sun Sparc Users
---

### Post by archetypo on 2006-06-25
There are no sparc linux binaries for FreeNX.

But has anyone figured out how to compile the freenx server from seveas sources?

Thanks in advance.

--- EDIT

Nevermind, got it. You can follow the PowerPC directions here: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX), but must install and use fakeroot in front of this line: apt-get -b source nx freenx

---

### Post by allnameswereout on 2006-06-28
Yup.

1) Add the Seveas URLs to your sources.list as explained
2) *sudo apt-get -b freenx nx*
3) Follow the advice on what headers you may need. I manually downloaded the necessary files and used debuild instead of apt-get -b.

That should do it. I made binary .deb from the files Seveas provided. It works marvelous. However you'll need to use a NX 1.5.x client. The official NX 2.x client will not work and the 1.5.x for Windows is gone so you need to use your favorite search engine to find it (and be sure to check MD5 of that if you're paranoid / in production environment).

---

### Post by archetypo on 2006-06-28
Yeah, built in and found the 1.5 version.  I'm cookin' now.

---

### Post by pedor on 2007-11-26
Can I compile the freenx client for Linux sparc? How?

---

### Post by daflame on 2007-11-27
If anyone would like more recent sources that work great, just let me know and I'll post them on the forum I setup for FreeNX 0.7.1 and nx-3.0:
[http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx](http://ubuntuforums.org/showthread.php?t=620057&highlight=freenx)

---

