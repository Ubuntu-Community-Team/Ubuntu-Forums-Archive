---
title: "I'm in a bit of a password pickle."
date: 2008-01-23
forum: Server Platforms
---

### Post by Cloudy on 2008-01-23
Right, so - I have this old, old Packard Bell PC. Hold all jokes, please. ;)

Anyway, I have a few documents I'd like to pull off of it before it goes to the storage heaven in the sky, but the deal is - I've forgotten both my user and root passwords. 

Here's where the pickle comes in - the CD drive on this old PC is totally busted. It doesn't work at all. Bearing in mind the fact that I can't boot from a live CD, chroot and change the password, what CAN I do? Is there any bypass or anything of the sort I could use, or any way to reset the root or user password without having to jack around with the CD-rom drive some more? I really am hoping there's some way, because I want to get these documents off before the PC goes into permanent storage.

Thanks for any help/suggestions


EDIT: btw, it's running Ubuntu 5.10 if it makes any sort of difference

---

### Post by burbankmarc on 2008-01-23
there's all kinds of ways to boot of a floppy disk. so you can just boot up off your floppy, chroot, and change the password.

check here for OS's that fit on a floppy 
[http://computerstuff.jdarx.info/content/floppycd-linux-distributions](http://computerstuff.jdarx.info/content/floppycd-linux-distributions)

Also, don't throw that box away yet! It has a lot of use in it left. NetBSD is great for this kind of stuff. Check out this guys web server running on a 33mhz box!
[http://mark.is-a-geek.org/](http://mark.is-a-geek.org/)

---

### Post by Cloudy on 2008-01-23
Hi burbankmarc,

I forgot to mention - the floppy drive on this machine doesn't work either. :( It's endured a lot of hardships, and I'm truly amazed it still boots at all!

---

### Post by gn2 on 2008-01-23
If it boots OK it's very easy to change the password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by burbankmarc on 2008-01-23
does it have usb ports?

also have you tried booting into single user mode?

---

### Post by Cloudy on 2008-01-23
> **burbankmarc said:**
> does it have usb ports?

also have you tried booting into single user mode?

Every time I try, either one of two things happens:


without appending "init=/bin/bash" everything boots up fine and I'm prompted for the root password.

However, if edit the GRUB entry to

> 
single init=/bin/bash


Whenever I boot up, I'm just greeted by a blank, black screen. I may be doing something wrong, but this is what I'm going off of:

[http://www.newlinuxuser.com/howto-bypass-a-forgotten-root-password/](http://www.newlinuxuser.com/howto-bypass-a-forgotten-root-password/)

---

### Post by Cloudy on 2008-01-23
> **gn2 said:**
> If it boots OK it's very easy to change the password: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

Whenever I enter recovery mode I'm still eventually prompted for the root password to do maintenace. :(

---

### Post by aysiu on 2008-01-23
How about physically removing the hard drive and putting it inside a computer that can boot from CD?

---

### Post by gn2 on 2008-01-23
Remove hard drive and fit in another PC or USB enclosure and copy files across?

---

### Post by Cloudy on 2008-01-23
Thanks, guys - but I just have this PC and my laptop. My Vaio bit the dust in mid-December. Im googling around, though, and I'm sure I can find a way to jury-rig it to work or I'm just doing something stupid that I'm not catching every time I enter single user mode. ;)

EDIT: Got it. Thanks for the help, suggestions, and toughing my ahurrr hurrrr 'tardation out with me. I was just missing ONE CHARACTER whenever I edited the kernel line.

---

### Post by burbankmarc on 2008-01-23
hmm... well as long as you append single to the END of the kernel line, it should work...

Try it without the init part.

And if all that fails, do you have another computer you can physically put the HDD in?

---

### Post by Cloudy on 2008-01-23
> **burbankmarc said:**
> hmm... well as long as you append single to the END of the kernel line, it should work...

Try it without the init part.

And if all that fails, do you have another computer you can physically put the HDD in?

Refer to the edit in my previous post ;)

Thanks to all three of you for the help! Big thanks.

---

