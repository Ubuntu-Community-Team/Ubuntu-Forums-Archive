---
title: "Slack installation problems"
date: 2008-06-14
forum: Slackware and derivatives
---

### Post by gbrener on 2008-06-14
Hi,

I am having some Slackware installation issues.  I am currently trying to install it with 3 CDs.  I downloaded three ISOs from Slackware's website which are burnt seperately, with one on each CD.

Anyway, I restart my computer and it gets to the boot screen, to which I press "enter".  I get in and log in as the root.  My problem occurs when I enter cfdisk to see my partitions.  It says that I have none, and *only *600-something MB available in free space, when in reality (according to Vista's disk management) have 20GB unallocated.  I tried going into setup, and it recognizes the space through that, but doesn't let me install after I go to "Target" and allow it for use.

Attached is a print screen I made that shows Vista's disk management with my partitions.  I'm not sure what the one on the far left is, but Vista won't let me manage that part for some reason.

---

### Post by cardinals_fan on 2008-06-15
That's strange... :confused:

---

### Post by Royajm on 2008-08-20
I have the exact same problem, though I have my whole hard drive formatted/unallocated (with dban) (totaling about 80 GB)
but Slackware's (okay Linux's) fdisk AND cfdisk both show only 4 gigs of unallocated space.
I can't even make a partition bigger than that... GParted on Ubuntu shows the whole 74.53 GiB of space. :confused:
Has anybody got a clue what's causing this?

I'm trying to install Slackware with Enlightenment on my HP Compaq nx7300 laptop (I think it's this one, I bought it with Xp though): [http://www.digital-fusion.co.uk/INU_Products/INU_ProdDetailsL9.ASP?ref=11689517&pnb=RU463EA]("http://www.digital-fusion.co.uk/INU_Products/INU_ProdDetailsL9.ASP?ref=11689517&pnb=RU463EA")


Edit: Nevermind, I was doing it wrong, just realized that I was trying to install it on my dvd-drive. /dev/sda was my hdd even though I thought it was /dev/hda..

---

### Post by Royajm on 2008-08-20
.

---

### Post by kk0sse54 on 2008-08-20
You can try setting up the partitions with another linux LiveCD and then start the slack installer and point it to those partitions to install on. Just make sure you aren't pointing to your DVD drive like Royajm :)

---

### Post by tommcd on 2008-08-21
Or get a gparted live CD [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) or parted magic CD [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php) and partition and format your hard drive for installing Slackware with that. Then you can skip the cfdisk part of the Slackware install and go right into installing packages.

It is good to create the free space with Vista's partition manager. Just format the partition with the file system of your choice with Gparted or Parted Magic, and you should be good to go.

---

