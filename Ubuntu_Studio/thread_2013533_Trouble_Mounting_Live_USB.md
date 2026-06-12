---
title: "Trouble Mounting Live USB"
date: 2012-07-01
forum: Ubuntu Studio
---

### Post by johny why on 2012-07-01
hello

i'm running puppy linux. I attempted to create a live USB using the live Ubuntu Studio live CD download, using each of the following methods. Here are my results:

[http://murga-linux.com/puppy/viewtopic.php?t=67235](http://murga-linux.com/puppy/viewtopic.php?t=67235)
Grub2 method fell back to the terminal line, and failed. 
the Grub4dos method said i must specify number of heads, and failed. 

[http://murga-linux.com/puppy/viewtopic.php?t=54826](http://murga-linux.com/puppy/viewtopic.php?t=54826)
the syslinux method hangs at a blinking cursor. 

any suggestions?
thanks!

---

### Post by sgx on 2012-07-02
AVLinux, Bodhi, and Mint ubuntu version should work with
unetbootin.

[http://www.bandshed.net/AVLinux.html](http://www.bandshed.net/AVLinux.html)

[http://linuxmint.com/](http://linuxmint.com/)

[http://forums.bodhilinux.com/](http://forums.bodhilinux.com/)

I think I just used the normal bodhi installer, and it works,
using the early-boot menu to launch. It is a small barebones
E17 ubuntu remix, very enjoyable.
Cheers

---

### Post by johny why on 2012-07-02
I was able to get unetbootin running on puppy Linux wine, by adding my USB drive as a floppy in wine configuration (first autodetect, then show Advanced settings, then change the USB drive to type Floppy).

Problem now is that netbootin fills up my tmp during the extract, killing my OS. So, now trying to synlink tmp to another partition with more free space. Running into trouble with that. Details:

[http://forum.winehq.org/viewtopic.php?p=77555#77555](http://forum.winehq.org/viewtopic.php?p=77555#77555)

---

### Post by sgx on 2012-07-03
[http://www.accella.net/create-a-linux-mint-12-bootable-usb/](http://www.accella.net/create-a-linux-mint-12-bootable-usb/)

You can also install wine on puppy using a .pet file, or choose
a puppy version that includes wine by default.

A wubi install of ubuntu Mint, 'mint4win' would be of good use
if you have a windows partition, lets you choose between
booting mint linux or windows.

[http://community.linuxmint.com/tutorial/view/687](http://community.linuxmint.com/tutorial/view/687)

Cheers

---

### Post by johny why on 2012-07-03
> **sgx said:**
> [http://www.accella.net/create-a-linux-mint-12-bootable-usb/](http://www.accella.net/create-a-linux-mint-12-bootable-usb/)
that's the unetbootin method. as i described, i have netbootin running on puppy with wine. I have used netbootin on windows many times. Is there something different in the link you provided?

> **sgx said:**
> You can also install wine on puppy using a .pet file, or choose a puppy version that includes wine by default.
as i described, i'm running wine already. Is there something new you are suggesting here?

> **sgx said:**
> A wubi install of ubuntu Mint, 'mint4win' would be of good use if you have a windows partition, lets you choose between booting mint linux or windows.
sorry, i do not understand how this will help me with the issue i described.

---

