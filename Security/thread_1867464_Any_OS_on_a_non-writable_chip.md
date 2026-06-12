---
title: "Any OS on a non-writable chip?"
date: 2011-10-23
forum: Security
---

### Post by TheNewbieGeek on 2011-10-23
I had a netbook that sucked but the cool thing about it is that it had the operating system burned on a non writable chip. The reason I thought it was cool is because how could a OS get infected with a virus if it can't rewrite the OS. Do handheld computers have this? Is it as good as it sounds. Thanks for helping out a noob.

---

### Post by whatthefunk on 2011-10-23
If the OS is non-writable, I would think you would loose a lot of customization options.  Also, you couldnt upgrade or update.  And I doubt that it would really do that much to prevent infections since most infections dont need to rewrite the OS.  A lot of infections either hide themselves somewhere or act as a normal program.

---

### Post by Lars Noodén on 2011-10-23
You could put your system on a SD chip and boot from that and use the built-in SSD for data.   Most SD chips have a rw/ro switch on the side that you could flip.  Just be sure that the partitions that are writeable are mounted [font=Courier New]noexec[/font].

---

### Post by TheNewbieGeek on 2011-10-25
> **Lars Noodén said:**
> You could put your system on a SD chip and boot from that and use the built-in SSD for data.   Most SD chips have a rw/ro switch on the side that you could flip.  Just be sure that the partitions that are writeable are mounted [FONT=Courier New]noexec[/FONT].

What is a SSD? How do you mount the partitions that are writeable to noexec. I am familiar with partitions but only in install where I choose the whole hard drive as a partition and then install the os. Could you explain or give a link to a tutorial that can guide me through it thanks.

---

### Post by Lars Noodén on 2011-10-26
> **TheNewbieGeek said:**
> What is a SSD? How do you mount the partitions that are writeable to noexec. I am familiar with partitions but only in install where I choose the whole hard drive as a partition and then install the os. Could you explain or give a link to a tutorial that can guide me through it thanks.

SSD is Solid State Drive, a disk with no moving parts. Usually netbooks have one of those instead of a traditional hard drive.  They tend to be smallish.

You can get a detailed description of what goes where by looking that the man page [hier (7)](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html).  /proc, /dev, /sys and /run get mounted in RAM, so the only directories you need to worry about are /home, /var, and /tmp.  / can be read-only.

To get a detailed description of the mount process, see the man page for [mount ( 8 )](http://manpages.ubuntu.com/manpages/oneiric/en/man8/mount.8.html).  Look specifically at noexec and exec.  

Once you've looked at hier( 7 ) and mount( 8 ) you'll have enough background to target your searching better.

---

### Post by HermanAB on 2011-10-26
The Ubuntu LiveCD is read only.

---

### Post by tubbygweilo on 2011-10-26
[Trusted computing]("http://yro.slashdot.org/story/11/10/23/1556206/uk-government-pushing-for-trusted-computing") may be a short way off and may answer some of your needs but it is not for [all]("http://www.gnu.org/philosophy/can-you-trust.html").

---

