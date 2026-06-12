---
title: "Too Much RAM"
date: 2009-06-26
forum: Wine
---

### Post by gchand7 on 2009-06-26
Can Ubuntu utilize 8gb of ram?  I have 8gb in my machine but when I check system monitor it only recognizes 3.2 gb.

---

### Post by mcduck on 2009-06-26
> **gchand7 said:**
> Can Ubuntu utilize 8gb of ram?  I have 8gb in my machine but when I check system monitor it only recognizes 3.2 gb.

If you have a 64-bit processor, and you install the 64-bit version of Ubuntu, then yes.

32-bit operating systems can't address more than 4GB of memory, and this includes memory addresses other than your RAM, like graphics card memory etc, so you get something around 3GB of accessible RAM.

(Well, you can always use PAE-enabled kernel like the server kernel to work around the limit, but PAE has it's downsides as well so I'd recommend going for real 64-bit instead)

---

### Post by snek on 2009-06-26
> **mcduck said:**
> If you have a 64-bit processor, and you install the 64-bit version of Ubuntu, then yes.

32-bit operating systems can't address more than 4GB of memory, and this includes memory addresses other than your RAM, like graphics card memory etc, so you get something around 3GB of accessible RAM.

(Well, you can always use PAE-enabled kernel like the server kernel to work around the limit, but PAE has it's downsides as well so I'd recommend going for real 64-bit instead)

McDuck is correct, if you want to be able to use more than 4GB ram you will have to change to the 64bit version of Ubuntu. **Be sure your CPU supports it though!**

---

### Post by gchand7 on 2009-06-26
AMD Phenom X4 9550 Asus M3A78 hdmi   DDR2 pc6400 800 mhz Geforce 512mb video card. I use this machine for video and music I have a 1.5 tb drive that I use as storage. This is fast on burning and video editing. Do you guys think the 64bit version would be better to install?

---

### Post by jimv on 2009-06-26
> **gchand7 said:**
> AMD Phenom X4 9550 Asus M3A78 hdmi   DDR2 pc6400 800 mhz Geforce 512mb video card. I use this machine for video and music I have a 1.5 tb drive that I use as storage. This is fast on burning and video editing. Do you guys think the 64bit version would be better to install?

Definately yes.  You want the 64bit.  It'll have to be a new install though, because you can't upgrade from the 32bit to the 64bit.

---

### Post by Bucky Ball on 2009-06-26
+1. 64bit it is.

---

### Post by mcduck on 2009-06-26
Yes, your system definitely supports 64 bits, and if you plan on working with any video/audio on Linux you'll get a nice performance kick from using 64-bit operating system in addition to extra RAM supported.

..besides, these days stuff like Flash and Java are easily available for 64-bit Linux as well, so there isn't really anything to loose. ;)

---

### Post by ericab on 2009-06-26
+1 on 64 bit!!

---

### Post by gchand7 on 2009-06-30
Ok installed the 64bit Ubuntu. Now when I try to install the libdvdcss2 it gives me an error of
wrong i386 any suggestions ?

---

### Post by Grishka on 2009-06-30
> **gchand7 said:**
> Ok installed the 64bit Ubuntu. Now when I try to install the libdvdcss2 it gives me an error of
wrong i386 any suggestions ?

[http://www.medibuntu.org/](http://www.medibuntu.org/).

---

### Post by Bucky Ball on 2009-06-30
> **Grishka said:**
> [http://www.medibuntu.org/](http://www.medibuntu.org/).

To that, I'll add this:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by gchand7 on 2009-07-01
Got everything back working now. Thank you everyone......

---

