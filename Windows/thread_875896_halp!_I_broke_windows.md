---
title: "halp! I broke windows"
date: 2008-07-31
forum: Windows
---

### Post by ruthiepoos on 2008-07-31
I've just installed ubuntu inside of windows (I couldn't create a partition for some odd reason). Anyway, while using Windows the other day, I picked up a virus/worm (hellmsn). I got rid of that but now when I try to boot Windows, I just get stuck in a perpetual loop of booting. I can get into ubuntu just fine though so it's not my PSU. I eventually want to get rid of Windows because I've had SO many problems with it. I use debian at university and I love it, I heard great things about ubuntu so I'm trying that.

Anyway, back to the point. I need to rescue some work files from Windows (I didn't back up in my haste -___-). I can't access the Windows network. Is there anyway I can repair Windows from Ubuntu? I am a total numpty at these sorts of things.

Cheers in advance, Ruth.




ps. I forgot to say. One major problem, i forgot my password for the bios menu, gah!

---

### Post by aeiah on 2008-07-31
if all you want to do is rescue files from your windows partition, you should be able to just look through your windows partition from inside ubuntu.

you'll have to mount your windows drive first if it isnt mounted though. im at work and havent time to go through things right now, but someone will probably give you the info. if not, you may find it easier to search for help on mounting a windows partition from inside ubuntu than for help fixing windows

edit: oh, and there are ways to reset the bios which usually involves removing the cmos battery, perhaps setting a few jumpers too etc. but it'll be easier to remember your password :p it may not even be too important to mess with your bios if its set up to say, boot from cd first then hdd or whatever.

---

### Post by Troll_the_Great on 2008-07-31
You installed Ubuntu inside windows?How? With virtual box, or via Wubi? And if your windows can't boot how can you access a program that is in it?

---

### Post by halitech on 2008-07-31
if your Ubuntu partition is working, there shouldn't be any reason to reset the BIOS password, unless you need to get in and change the boot order so you could use the live cd to get the files you need instead of just mounting the windows partition from Ubuntu

---

### Post by halitech on 2008-07-31
> **Troll_the_Great said:**
> You installed Ubuntu inside windows?How? With virtual box, or via Wubi? And if your windows can't boot how can you access a program that is in it?

I have a feeling he's talking about using WUBI to install as he says he can boot into Ubuntu

---

### Post by Troll_the_Great on 2008-07-31
> **halitech said:**
> I have a feeling he's talking about using WUBI to install as he says he can boot into Ubuntu

Anyway, If he can boot into Ubuntu it shouldn't be any problem saving his data.
Have a look at this links for mounting windows partitions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
In the worst case, just boot with the live CD, search whatever data you need and save it on a DVD or an USB drive.
Cheers!

---

### Post by ruthiepoos on 2008-07-31
*she 

I have the installation disk for ubuntu 8.04 desktop edition. Originally, I wanted to create a partition half & half, but I couldn't do that from the CD, so I chose the option to install inside of Windows instead.

thanks for the pointers!

---

### Post by halitech on 2008-07-31
opps, sorry :( I seldom look at names and just use the generic he meaning everyone, bad habit I know

---

### Post by Sef on 2008-07-31
> opps, sorry :( I seldom look at names and just use the generic he meaning everyone, bad habit I know

That's why I like to use they as singular.  This has been done for centuries in English including writers like Chaucer and Shakespeare.

Moved to Windows forum.

> ps. I forgot to say. One major problem, i forgot my password for the bios menu, gah!
Last edited by ruthiepoos; 19 Minutes Ago at 10:14 PM. Reason: thought it was important you all should know how stupid I am. 

Forgetting your password is just being human, and nothing more.

---

### Post by linux_tech on 2008-07-31
Depends on whether you want to keep windows or not. If yo do then you can either use the windows install disk, boot to it and select non destructive install, this should repair the mbr or you can try to repair the mbr another way-
boot up using windows bootable floppy disk....
a:\> fdisk /mbr
this will fix MBR ..... and you will able to boot windows.....

But sounds like ubuntu install just over wrote the mbr and
the windows files are still there, just load ubuntu and access the files.

---

### Post by ruthiepoos on 2008-07-31
thanks.

I know that I can use the Windows disk, but I'm impatient, Its currently elsewhere. I need to update my portfolio for a job interview :s Hence why I need it. 

lessons have been learnt!

I'm following [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) and got as far as editing the the fstab file. Mine looks completely different to their example!

should look like:

> 
proc /proc proc defaults 0 0
/dev/hda6 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda1 /media/hda1 ntfs defaults 0 0
/dev/hda7 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0 

but mine looks like:
> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



---

### Post by LinuxRocks713 on 2008-07-31
> **ruthiepoos said:**
> <snip size="medium"></snip>

but mine looks like:
```

# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

```


That's because you are using Wubi.

---

### Post by ruthiepoos on 2008-07-31
aye i misunderstood. 

I can see my windows folder on the network, but there's nothing in it apparently. Whereas before this dumb virus, I could see all my files.

---

