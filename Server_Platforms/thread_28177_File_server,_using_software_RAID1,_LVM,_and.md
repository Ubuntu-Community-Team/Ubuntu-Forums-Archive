---
title: "File server, using software RAID1, LVM, and ?"
date: 2005-04-19
forum: Server Platforms
---

### Post by upgrdman on 2005-04-19
I'm new to Ubuntu and Debian in general, so maybe this plan of mine is not so smart, but I think it will be a nice way to learn, and since my fileserver is not mission critical yet, if I mess up, only good will come of it.

I have built a nice PC which will be used solely as a file server for my home LAN. I had a hard drive fail on me, so I decided to make a file server which has 4x 250GB hdd's. It will use RAID 1 (mirroring) so my data will be more resilient to future HDD failures, so I should end up with approx. 500GB of useable space. Right now I have 3 of the 4 HDD's, so I wanted to use LVM so I can later add to my first RAID 1 pair of disks. After my warrenty replacement for this failed hdd's comes back, it will be the 4th HDD, and I will make a RAID1 array out of it and the other remaining HDD.

To make myselft more clear, here is my goal in the end:

* Each of the first 2 HDD's will have two partitions: one for "/" and for "/data"
* The last 2 HDD's will have just one partition "/data"
* Each of the "/" and "/data" partitions of disks 1 and 2 will be using RAID 1
* The "/data" partitions on disks 3 and 4 will be using RAID 1
* LVM will be used to combine the "/data" RAID1 partitions for the two pairs of HDDs
* So this mean I will have only one "/data" ... a LVM group of the "/data" partitions

I have never used LVM before, so I could use some tips.

I installed ubuntu on my laptop, and recall seeing some stuff for RAID and maybe even LVM when setting up my partitions on my laptop... is that all I need to play with when I install ubuntu on my new file server?

Lastly, I am not sure what to use to serve the "/data" partition... Win32 compatibility would be nice, but not required. My main concern is that I be able to share "/data" as read-write to anyone on my network, with some authentication. To keeps things sane, I would like my fileserver to automatically make all files have the same UID/GID so that files created by different users on different PCs on my LAN won't be a headache of different UIDs/GIDs, like I had when I tried NFS a while ago. All files put into "/data" will be for the same thing, so there is no real reason to restrict file permissions to anyone, except that people will need to have a way to authenticate, so that my file server will not be blinding vulnerable to a unwanted person with access to my LAN.

Sorry for the long post and slew of questions :)

Thanks,
--Farrell F.

---

### Post by tonym on 2005-04-19
What you are proposing is quite possible.  Just a couple of thoughts:

It's possible to put your / partition in LVM on RAID.  This might make things more flexible in future.

If you did the above,  you could be adventurous and try RAID1+0  (or is it RAID0+1).  Pair your drives in RAID1 mirrors.  Then pair the two /dev/md* devices in RAID0 striping which is supposed to give some performance benefits.  Then put LVM on top.  There are problems putting /boot on LVM so you might need to put some small partitions at the start of the drives for /boot.   These can be RAID1.

Even though you have only got three drives,  you could set up the above with one array degraded and then hot add when you have the new drive.

For sharing,  you say you need access by Windows PCs so you need to look at SAMBA.  After you have installed it there will be a skeleton config file set up for you to edit/add to  -  its reasonably well commented.

Regards

Tony.

---

### Post by upgrdman on 2005-04-19
OK, but I don't think "/" will be a big issue, because i plan to set aside 10GB for it, and its will only be for programs, etc.

My main question is just ... how? I'm new to Ubuntu/Debian. Like I said, I recall something about RAID and maybe even LVM when I was installing ubuntu on my laptop... is that all I would need to play with, until I get my 4th drive back? And then what would I need to do to use the last 2 hdd's with RAID1 and add it to the LVM group?

Thanks,
--Farrell F.

---

### Post by adeh on 2005-04-20
I have spent a lot of time setting up debian servers as file servers with RAID. I had enough problems with RAID that I was not even going to try LVM until I had more drives. In both cases I have a new motherboard and 2 120GB drives that I set up for RAID1.

The process for raid on Debian was not so straightforward. The tools included in the installer do not seem to work at all, in my experience (i could be wrong/stupid). You have to install your base system on one drive, then once you get in, configure the other partitions and set up the RAID manually. After the 4th time I had re-installed debian, I had it down pretty good.

The HOWTO I used was here :
[http://alioth.debian.org/download.php/668/rootraiddoc.97.html](http://alioth.debian.org/download.php/668/rootraiddoc.97.html)

The only GOTCHA deals with booting into your raid disk from lilo (the default in debian). But to solve it, I just followed the instructions for initrd that were listed in the GRUB section, and finally it worked fine.

I just noticed that one of my old bookmarks has been updated, with good news:
[http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html](http://xtronics.com/reference/SATA-RAID-debian-for-2.6.html)

Maybe the Hoary installer will work better for you.

For sharing, i recommend SAMBA. It is pretty easy to set up as a stand-alone file server. Using it as a PDC is hard though. 

Good luck!

-Adeh

---

### Post by LazyBoy on 2005-04-24
I've only done one RAID install and that wasn't on Ubuntu, so I'm far from an expert.  But for a first timer I would recommend:

1)  Don't put / on a RAID.  It's considerably harder than the other partitions
and / can be replaced (with a reinstall) easier than your data.  Then you can concentrate on RAID issues from a fully installed OS.

2)  If you're going SATA (I did), you may have issues to work out there before you move on to RAID.  There were **major** changes between the 2.4 and 2.6 kernels for SATA support. (I had a PCI SATA card that took some tweaking.)

3)  Leave room for an alternate / partition.  It'll be good in the future when you change distros or do a major upgrade.

4) Test RAID failure and notification before you put your data on.

5) LVM is cool, but it's kind of the opposite of RAID.  Do you really need to combine your two data partitions?  Then you don't know where a file really is.  What happens when a disk fails?  If two disks fail?

Have you considered 3 250G in RAID 5 = 500G + another disk for / ?  An old 40G could be your /  .

LB

---

