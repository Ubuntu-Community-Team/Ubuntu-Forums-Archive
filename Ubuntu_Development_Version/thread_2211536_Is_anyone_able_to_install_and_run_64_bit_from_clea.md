---
title: "Is anyone able to install and run 64 bit from clean install?"
date: 2014-03-16
forum: Ubuntu Development Version
---

### Post by sdowney717 on 2014-03-16
I am thinking maybe of installing 64 bit 13.10 then upgrading online to 64 bit 14.04

Last week could not install and run  14.04 64 bit, nothing is any better

---

### Post by 23dornot23d on 2014-03-16
I installed the 64 bit the other day and it was a clean install ... all went well .... just the sound was missing on mine
but rectified it . If you check out on conky it will show what version etc in the screenshot below.

But it runs really smoothly and quickly too ....

[IMG]http://i.minus.com/ibv5f6td2KjFpb.png[/IMG]

Asus K53SV laptop with optimus ...... the kernel version was the  -17 ......

Todays screen is different background - but same install

[IMG]http://i.minus.com/ibnae3JoDjTgXT.png[/IMG]

K53SV:~$ uname -a
Linux keith-K53SV 3.13.0-17-generic #37-Ubuntu SMP Mon Mar 10 21:44:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by sdowney717 on 2014-03-16
I just verified this PC here CAN run 64 bit 13.10, install and ran it just now.
Boots up no errors.

There must be a bug in the 64 bit installer. MB is MSI 7529 with an e6550 CPU and AMD x1650 pro GPU, 4 GB ddr2, 200gb WD2000 and cdrom drive and nothing else.

I will try and do an upgrade to 14.04 now.

> boat@boat-MS-7529:~$ uname -a
Linux boat-MS-7529 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
boat@boat-MS-7529:~$ 



Installed with seperate /home from /

link to post showing boot error.
[http://ubuntuforums.org/showthread.php?t=2211519](http://ubuntuforums.org/showthread.php?t=2211519)

---

### Post by kansasnoob on 2014-03-16
I haven't tried any amd64 images since the flavors released their Beta 1 images, but late last night and early this AM I tried Lubuntu, Ubuntu, and Ubuntu GNOME i386 images and they all failed - that is the Check disc for defects always returned "1 error found" so I then tried testing the same images with Testdrive + Virtualbox in a Precise host after checking md5sums and they all failed :(

I'm just now going to try a new Ubuntu build but zsync is crawling along:

[ATTACH=CONFIG]251210[/ATTACH]

I'm hoping that someone just threw a bad ingredient in the recipe :lolflag:

---

### Post by QDR06VV9 on 2014-03-16
> **kansasnoob said:**
> I haven't tried any amd64 images since the flavors released their Beta 1 images, but late last night and early this AM I tried Lubuntu, Ubuntu, and Ubuntu GNOME i386 images and they all failed - that is the Check disc for defects always returned "1 error found" so I then tried testing the same images with Testdrive + Virtualbox in a Precise host after checking md5sums and they all failed :(

I'm just now going to try a new Ubuntu build but zsync is crawling along:

[ATTACH=CONFIG]251210[/ATTACH]

I'm hoping that someone just threw a bad ingredient in the recipe :lolflag:

Rounding to  Home only 24Hrs to Go!! Speed Demon you:lolflag:

---

### Post by kansasnoob on 2014-03-16
> **runrickus said:**
> Rounding to  Home only 24Hrs to Go!! Speed Demon you:lolflag:

The choking ain't on my end:

[ATTACH=CONFIG]251211[/ATTACH]

I suspect that the zsync server is just tied up with uploads of new images ;)

---

### Post by sdowney717 on 2014-03-16
installing Saucy 64 bit and then upgrading to Trusty works!:p

So now I have 64 bit trusty and can set it up.

---

### Post by jerrylamos on 2014-03-16
I do tahr 64 bit installs on netbook and notebook and 32 bit on a tower every couple weeks or so.  Late last month there was a week when the installs didn't work.  Last ones I did worked.

You can expect bugs on the development level U+1 - even serious - right up to release and in the past, past release even.  Maybe a couple weeks after release it might be solid.

---

