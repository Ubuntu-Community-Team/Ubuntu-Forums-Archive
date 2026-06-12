---
title: "Precise Pangolin latest build ISO would not boot"
date: 2012-03-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by glentrobfc on 2012-03-27
I tried to test the latest build with a flash set up with unetbootin.  It booted fine on my netbook (HP mini 210), but stopped booting on a Dell Inspiron 600m with the message that PAE was required.  I did not expect that on the i386 version.  This same Dell is running Mint 12 KDE, MEPIS, and Windows XP.  Is Ubuntu going to stop supporting earlier Ix86 processors?

---

### Post by oldos2er on 2012-03-27
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by Scott Baker on 2012-03-27
This could be an issue. I tried to boot 12.04 Beta through V-Box a couple of days ago, and got the EXACT SAME  error message. Thought it might have hiccuped when loaded to my USB, so I reloaded it on to the USB, but no luck, same error message. ](*,)

---

### Post by grahammechanical on 2012-03-27
The powers that be have decided that the i386 version of Ubuntu is now pae enabled by default. They will not be providing a non-pae i386 kernel ISO image.

I think that it is intended for Xubuntu to have a non-pae kernel available. 

Regards.

P.S. I tested Ubuntu Studio i386 and that also had a low-latency pae kernel. I also test Xubuntu but that did show up as a pae kernel.

P.P.S. Please check these threads:

[http://ubuntuforums.org/showthread.php?t=1924455]("http://ubuntuforums.org/showthread.php?t=1924455")

[http://ubuntuforums.org/showthread.php?t=1943276]("http://ubuntuforums.org/showthread.php?t=1943276")

[http://ubuntuforums.org/showthread.php?t=1938684]("http://ubuntuforums.org/showthread.php?t=1938684")

---

### Post by jerrylamos on 2012-03-28
Currently lubuntu has a non-pae kernel.  Try it.  Fast!  Easy!  Capable!

Haven't tried installing the unity desktop on lubuntu.

Now ubuntu Install has the option to download updates.  So far ubuntu development refuses to consider downloading the kernel that fits the hardware.  They could.

Ubuntu development doesn't care about us judging from their actions and lack of communication.  

They are concentrating on making ubuntu look like a tablet or a smartphone as a way of increasing ubuntu footprint.

There are a "lot of fish in the ocean".  I've been running ubuntu mostly because I like the forums.

Jerry

---

