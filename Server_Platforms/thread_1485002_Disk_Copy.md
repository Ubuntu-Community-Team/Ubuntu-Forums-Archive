---
title: "Disk Copy"
date: 2010-05-16
forum: Server Platforms
---

### Post by Vegan on 2010-05-16
yesterday I was able to copy my Windows install onto a new bigger disk and it took only an hour to do it. So now I have more space, fine.

So is there a tool for Linux to do what I did with Windows?

Clone a disk?

---

### Post by ian dobson on 2010-05-16
Hi,

Have a look at dd, abit like copy for whole devices.

Regards
Ian Dobson

---

### Post by Vegan on 2010-05-16
That tool is meant for file conversions. I was more interessted in cloning the disk onto the new disk.

Its not a big deal as I am skilled enough to have a server back up in about 2 hours from a blank HD and a Ubuntu CD.

---

### Post by koenn on 2010-05-16
> **Vegan said:**
> That tool is meant for file conversions. I was more interessted in cloning the disk onto the new disk.

nope, it works on block devices - disks and such

[http://ss64.com/bash/dd.html](http://ss64.com/bash/dd.html)

examples :
Clone one hard drive onto another
$ dd if=/dev/sda of=/dev/sdb

---

### Post by frostschutz on 2010-05-16
cloning a disk is one of the most trivial tasks imaginable, you can do it in less than 10 lines of code... but most people just use dd ;)

of course there are also more elaborate solutions, for example partimage (omits 'free space' of known filesystems), or clonezilla (livecd/usb), or lots of others...

but once you are familiar with dd you'll pretty much always use dd since it's available everywhere and the most versatile solution

that, and rsync - if you need to only copy files (ie. when cloning a linux system)

---

### Post by Vegan on 2010-05-16
Right now I use SAMBA and I backup the Linux box to a disk on the Windows machine. All I need are the Apache2 settings file, and the web folder, rest is factory fresh. SAMBA is setup with Webmin and I have the setup for that saved too.

With Windows its a real pain in the butt to install fresh and then install all the software.

So I wrote a page on my site and I was thinking how could a this be done or Linux without major problems.

I use the sever edition. I have looked at the desktop a bit and I did not see real freedom from the CLI.

So as far as I see it, the CLI is fine sans desktop.

All I use Linux for is my web server.

---

### Post by xkaliburx on 2010-05-16
If you want simple, just downlaod the clonezilla .iso, burn, boot off it and your done.  [http://www.clonezilla.org/]("http://www.clonezilla.org/") is where you can find it, and basically it's a ghost app where you can do one of the following;

Boot off the CD, make an image of the hard drive on another hard drive, samba mount, nfs mount, etc.  Or do a disk -> disk dupe.

Really a few command line answers and your off to the races!  Basically it's a basic front-end to DD, but real simple to use.

---

### Post by Vegan on 2010-05-16
Thanks, that Clonezilla looks attractive. My goal is simple, to be able to clone the old disk on to a bigger disk to save time etc.

So given /dev/sda as the existing disk and /dev/sdb as the new disk that is say 2x larger, I can then clone the system, remove the old disk, and reboot with the new bigger disk.

That is more or less that way Windows based cloning works, and it looks like Clonezilla can do the job.

---

### Post by windependence on 2010-05-17
I can do that in one line:

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerror
```

Best dd info on the net:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

-Tim

---

### Post by Vegan on 2010-06-22
Can that DD command run from the Live Ubuntu CD so that the Linux box is down and safe to copy?

---

### Post by bertmanphx on 2010-06-22
Vegan,
I think it will run from the Live CD just fine.  But it would run a lot faster if you just plugged that drive into a USB external adapter, and copied it that way.

+1 for Clonezilla

bertmanphx

---

### Post by BobVila on 2010-06-22
It'll run from the LiveCD fine. No idea what bertman is on about with the external USB adapter, as that would be around infinity times slower than having them plugged into the motherboard. If you've got both of these disks plugged into the motherboard, boot the LiveCD and use dd. 

You can look into clonezilla, but if you're just one-off copying a disk, use dd and be done with it.

---

### Post by bertmanphx on 2010-06-22
I apologize if i was not clear.

Assuming he had another computer with Linux installed, I was proposing that he remove the drive, and plug it into a sata/usb external drive enclosure.  Thenn use the DD command from a fully running OS.  The thought being that it would be faster than running from a live CD.

---

