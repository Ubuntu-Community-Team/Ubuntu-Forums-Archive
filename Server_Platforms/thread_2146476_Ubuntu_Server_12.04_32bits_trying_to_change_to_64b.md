---
title: "Ubuntu Server 12.04 32bits trying to change to 64bits"
date: 2013-05-18
forum: Server Platforms
---

### Post by djjonex on 2013-05-18
How I know if my computer is 64bits?

Right now I have Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-28-generic i686).
Is there any command that let me know if I'm able to install Ubuntu Server 64bits?

The purpose of this  move is that I have 4Gb RAM (2Gb X 2) and 32bits only read 3Gb...
Other Specs from my computer:
Model: Dell Optiplex 210L
Intel Pentium 4
80Gb HD

A friend told me about using PAE but I'm not familiar with the process.  If somebody can help me with this I'll appreciate.

---

### Post by mörgæs on 2013-05-18
Please run ```
sudo lshw > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by djjonex on 2013-05-18
I pasted it here [http://pastebin.com/GUtqrsmm](http://pastebin.com/GUtqrsmm)
since is very long output.

Thanks,

Jonex

---

### Post by mörgæs on 2013-05-18
Yes, it does support 64 bit. You have to reinstall, because a 32 bit installation can not be upgraded to 64.

---

