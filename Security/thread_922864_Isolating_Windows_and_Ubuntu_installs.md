---
title: "Isolating Windows and Ubuntu installs"
date: 2008-09-17
forum: Security
---

### Post by flatland2d on 2008-09-17
I'm trying to help a friend get set up with Ubuntu.  He has Windows on one hard drive, and Ubuntu on a separate hard drive.  He wants to make sure there is 100% isolation between the two operating systems (ie, no files on Ubuntu drive, including possible Windows viruses, that could affect the Windows drive, and visa versa).  What can I tell him about how to set this up?

---

### Post by gali98 on 2008-09-17
As far as I know, Windows will not even see the Ubuntu drive as it does not have a driver for ext3 (linux's main filesystem.)
Also make sure that when he (or you) install ubuntu, to put the bootloader on the drive ubuntu has. The easiest way to make sure is to unplug the windows drive when installing. (before booting, not during :)) That will leave no room for error.
Whenever booting he will have to press the select boot key (different on every computer, try delete, and the f keys)
That should be safe enough.... but some others may have other opinions.
If that is not enough, he should install a virus scanner on ubuntu....
Kory

---

### Post by flatland2d on 2008-09-17
He installed Ubuntu already.  Any way to check which drive the bootloader is on?  Also, why does this matter?

---

### Post by gali98 on 2008-09-18
Well to technically be entirely separate the boot loader for ubuntu would be on the ubuntu drive and the windows bootloader on the windows drive.
It isn't that big a of a deal unless your friend is a security pshyco.
I guess the way to check is when booting, go to the boot device selector. (it will have cd, usb, network, the hard drives and maybe more in a list.)
And just boot each drive. One will have grub on it... There is probably some command you can run, but I don't know one.
I would not worry about it.

Kory

---

### Post by hyper_ch on 2008-09-19
don't forget, that malware on windows can still format the whole linux drive... there's no "seeing" needed...

---

### Post by gali98 on 2008-09-19
True...
The only way to be completely separate is for you to unplug the other os's hard drive while using the os. Unless of course the hacker sends his hard drive monkeys after you... Beware

Kory

---

### Post by Titomarques on 2008-09-20
How do i put the ubuntu loader on ubuntu partition, the SO don't let me choose? It automactly puts (hda0), if so i had to change this to sda6 (where is my ubuntu partition), i'm trying that now, maybe work i don't now!! Next you can use bootpart to choose the first loader an so on.

---

### Post by gali98 on 2008-09-20
The bootloader does not go on a partition. It goes on a hard disk. If you only have one drive it will go on there.
It is not a partition.....
So you can't really put it on sda6... Techinically it goes on just sda (or sdb and so on)

Kory

---

