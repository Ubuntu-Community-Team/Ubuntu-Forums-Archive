---
title: "HOW TO: mount /tmp to ram for increased preformance."
date: 2009-01-29
forum: Tutorials
---

### Post by modmadmike on 2009-01-29
If you watch a lot of youtube video's or run a lot of programs that cache to /tmp you will notice that it can be incredibly slow while multi-tasking because the other programs are using the disk too. As long as you have enough ram you can mount /tmp as to your ram. However, use at your own risk - programs that cache backup data to /tmp (Like firefox [although open office does not]) will not be able to restore your previous session after rebooting. If that is no problem then continue on reading.

Open your /etc/fstab as root in your favourite text editor (I will be using gedit because it is by far the most simple) by launching it from the terminal.
```
sudo gedit /etc/fstab
```

Add this line to the end.
```
##RAMDISK##
none /tmp tmpfs defaults,size=424m 0 0
```
You can change the size to whatever amount you want in megabytes but do not go over half of your ram. <Ctrl>+<s> and <Ctrl>+<q>

Reboot, yes this is needed, you can mount -a but its pointless because then your xserver will crash because the display property will become unset.

Enjoy much faster website loads!

Also a tip for youtube users, the video is stores in /tmp so you dont need to use a flash down-loader to save a youtube video - just copy the file to your folder of choice after watching it.

EDIT*

The size parameter is optional as I have found out from experience so you might want to use this instead to save RAM!
```
##RAMDISK##
none /tmp tmpfs defaults 0 0
```

EDIT**

Okay I just found out how to do this without rebooting but its not quite as simple. Continue from the last step before rebooting, exit everything, and <ctrl>+<F1>. Enter your username and password. Run these commands.
```
sudo -i
gdm stop
rm -fR /tmp/*
mount /tmp ##or mount -a
gdm restart
```

EDIT***
Do not use this trick if you use proprietary types of enterprise software, because they store files in /tmp for security reasons.

---

### Post by waster on 2009-03-27
not sure about the value of this (RAM caches disk anyway), but you certainly don't need the 1 and 2 at the end.


From man /etc/fstab:

       The fifth field, (fs_freq), is used for these filesystems by the dump(8) com&#8208;
       mand to determine which filesystems need to be dumped.  If the fifth field is
       not present, a value of zero is  returned  and  dump  will  assume  that  the
       filesystem does not need to be dumped.

       The sixth field, (fs_passno), is used by the fsck(8) program to determine the
       order in which filesystem checks are done at reboot time.  The root  filesys&#8208;
       tem  should  be specified with a fs_passno of 1, and other filesystems should
       have a fs_passno of 2.  Filesystems within a drive will  be  checked  sequen&#8208;
       tially,  but filesystems on different drives will be checked at the same time
       to utilize parallelism available in the hardware.  If the sixth field is  not
       present  or  zero,  a value of zero is returned and fsck will assume that the
       filesystem does not need to be checked.

---

### Post by modmadmike on 2009-03-27
oh noes!!!!!!!!!! my /etc/fstab disappeared after using webmin (and looking to update it)!!!!!!!!!!!! better not restart no matter what till I fix this lol!

---

### Post by modmadmike on 2009-03-27
oh phew I just typed /ect/fstab instead of /etc/fstab rofl

---

### Post by Bossieman on 2009-04-02
Thanks! Works like a charm!

---

### Post by dcstar on 2009-04-03
> **modmadmike said:**
> If you watch a lot of youtube video's or run a lot of programs that cache to /tmp you will notice that it can be incredibly slow while multi-tasking because the other programs are using the disk too. **As long as you have enough ram you can mount /tmp as a ramdisk.**
.......

A tmpfs mount is **NOT** a "ramdisk" mount. A "ramdisk" is a totally different thing that is set up with a kernel boot parameter and removes a set amount of RAM for use.

A tmpfs mount will use your Virtual Memory as required, which will be RAM as well as Swap, so in a heavily loaded system it could well be using disk space.

[http://en.wikipedia.org/wiki/TMPFS](http://en.wikipedia.org/wiki/TMPFS)

Using /tmp in this manner can certainly improve "performance", but it also can cause issues in things like DVD creation if a temporary image file (~8GB) happens to be created in that folder.....

---

### Post by Cowchip7 on 2009-04-16
I am thinking about trying this out, since I have 2gb ram. If I wast to reverse the changes I made, I am assuming I would only have to enter:

sudo gedit /etc/fstab

and then delete the following line of code (the code I previously added). Is that correct?

##RAMDISK##
none /tmp tmpfs defaults 0 0
:popcorn:

---

### Post by binbash on 2009-04-16
> **Cowchip7 said:**
> I am thinking about trying this out, since I have 2gb ram. If I wast to reverse the changes I made, I am assuming I would only have to enter:

sudo gedit /etc/fstab

and then delete the following line of code (the code I previously added). Is that correct?

##RAMDISK##
none /tmp tmpfs defaults 0 0
:popcorn:

Yep

---

### Post by modmadmike on 2009-04-28
> **dcstar said:**
> A tmpfs mount is **NOT** a "ramdisk" mount. A "ramdisk" is a totally different thing that is set up with a kernel boot parameter and removes a set amount of RAM for use.

A tmpfs mount will use your Virtual Memory as required, which will be RAM as well as Swap, so in a heavily loaded system it could well be using disk space.

[http://en.wikipedia.org/wiki/TMPFS](http://en.wikipedia.org/wiki/TMPFS)

Using /tmp in this manner can certainly improve "performance", but it also can cause issues in things like DVD creation if a temporary image file (~8GB) happens to be created in that folder.....

Thanks for pointing that out, but at the time it seemed simpler to use the term "ramdisk" lol

---

### Post by modmadmike on 2009-10-11
Deleted

---

### Post by yakshbuntu on 2011-08-13
> **modmadmike said:**
> If you watch a lot of youtube video's or run a lot of programs that cache to /tmp you will notice that it can be incredibly slow while multi-tasking because the other programs are using the disk too. As long as you have enough ram you can mount /tmp as to your ram. However, use at your own risk - programs that cache backup data to /tmp (Like firefox [although open office does not]) will not be able to restore your previous session after rebooting. If that is no problem then continue on reading.

Open your /etc/fstab as root in your favourite text editor (I will be using gedit because it is by far the most simple) by launching it from the terminal.
```
sudo gedit /etc/fstab
```

Add this line to the end.
```
##RAMDISK##
none /tmp tmpfs defaults,size=424m 0 0
```
You can change the size to whatever amount you want in megabytes but do not go over half of your ram. <Ctrl>+<s> and <Ctrl>+<q>

Reboot, yes this is needed, you can mount -a but its pointless because then your xserver will crash because the display property will become unset.

Enjoy much faster website loads!

Also a tip for youtube users, the video is stores in /tmp so you dont need to use a flash down-loader to save a youtube video - just copy the file to your folder of choice after watching it.

EDIT*

The size parameter is optional as I have found out from experience so you might want to use this instead to save RAM!
```
##RAMDISK##
none /tmp tmpfs defaults 0 0
```

EDIT**

Okay I just found out how to do this without rebooting but its not quite as simple. Continue from the last step before rebooting, exit everything, and <ctrl>+<F1>. Enter your username and password. Run these commands.
```
sudo -i
gdm stop
rm -fR /tmp/*
mount /tmp ##or mount -a
gdm restart
```

EDIT***
Do not use this trick if you use proprietary types of enterprise software, because they store files in /tmp for security reasons.

Thanks

---

### Post by DroidVPN on 2011-12-01
> **dcstar said:**
> A tmpfs mount is **NOT** a "ramdisk" mount. A "ramdisk" is a totally different thing that is set up with a kernel boot parameter and removes a set amount of RAM for use.

A tmpfs mount will use your Virtual Memory as required, which will be RAM as well as Swap, so in a heavily loaded system it could well be using disk space.

[http://en.wikipedia.org/wiki/TMPFS](http://en.wikipedia.org/wiki/TMPFS)

Using /tmp in this manner can certainly improve "performance", but it also can cause issues in things like DVD creation if a temporary image file (~8GB) happens to be created in that folder.....

Do you know how to setup a real ramdisk?

---

