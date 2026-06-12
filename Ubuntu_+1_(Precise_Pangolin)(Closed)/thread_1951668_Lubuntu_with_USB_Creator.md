---
title: "Lubuntu with USB Creator"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by uRock on 2012-04-02
I have tried to use Startup Disk Creator to create a bootable image of Lubuntu 12.04 with no success. Is it normal for Betas to not work with Startup Disk Creator? I ended up using Lubuntu 11.10, but it'd be nice to know.

---

### Post by nm_geo on 2012-04-02
sudo dd if=precise-alternate-amd64.iso of=/dev/sdb> **uRock said:**
> I have tried to use Startup Disk Creator to create a bootable image of Lubuntu 12.04 with no success. Is it normal for Betas to not work with Startup Disk Creator? I ended up using Lubuntu 11.10, but it'd be nice to know.

I have used the Startup Disk Creator a number of times during this cycle to create persistent USB drive versions for testing.  However since Colin Watson made the iso bootable hybrids I normally use the following without persistence.


Create bootable USB PP since 11/25/2011 and forward

In terminal cd isos/lus (where I keep my zsync copies of lubuntu precise)

```
sudo dd if=precise-desktop-amd64.iso of=/dev/sdb
```

and 

```
sudo dd if=precise-alternate-amd64.iso of=/dev/sdb
```

Your sdx may be different than mine. I typically reformat my flash drive with fat32 before writing the iso.

In addition the flash drive completes in 6 minutes depends on the write speed of the flash drive.

---

### Post by uRock on 2012-04-02
nm_geo, do I keep the **if=** in the command when running it?

Thank you for the knowledge.

---

### Post by nm_geo on 2012-04-02
I keep thinking of things to say.. :lolflag:

I made one tonight with the dd command and ran a live USB test and manual install with the 20120402 current daily build they are logged on qa tracker.

[http://iso.qa.ubuntu.com/qatracker/milestones/Testing](http://iso.qa.ubuntu.com/qatracker/milestones/Testing)

---

### Post by nm_geo on 2012-04-02
> **uRock said:**
> nm_geo, do I keep the **if=** in the command when running it?

Thank you for the knowledge.

 Yes if you copy the command it is correct as long as you are in the correct directory.  I may try to make a one with the usb-creator in a bit too.  Will log back if I have a problem.

---

### Post by uRock on 2012-04-02
Thanks again for sharing.

---

### Post by cariboo on 2012-04-02
Just to add a bit of info as far as the command options go,

if = input file
of = output file

You can also use the same command to create an iso image of a cdrom for example:

```
dd if=/dev/sr0 of=name_of_cdrom.iso
```

I used to create and store iso images of cdroms that I use all the time, as they are so susceptible to damage.

---

### Post by uRock on 2012-04-02
> **cariboo907 said:**
> Just to add a bit of info as far as the command options go,

if = input file
of = output file

You can also use the same command to create an iso image of a cdrom for example:

```
dd if=/dev/sr0 of=name_of_cdrom.iso
```

I used to create and store iso images of cdroms that I use all the time, as they are so susceptible to damage.

Good to know, thanks! :p

---

### Post by nm_geo on 2012-04-02
> **uRock said:**
> Thanks again for sharing.

uRock you probably don't want to hear this but I just made a persistent USB with Lubuntu precise desktop amd64.  Booted it up added my b43 firmware that I always have on another stick. Connected to my wifi and imported my Google settings and I am using it right now to write this. 

Maybe your flash drive has a problem.. I don't know but I hope both methods work for you in the future. I find the dd method saves me lots of time during testing, but many users say it is too old and dangerous. Thus the nickname disk destroyer.. 

See screenshot..

---

### Post by uRock on 2012-04-02
I was trying to create the installer with persistance. That may have been the issue. I have faith in the cli you gave me getting the job done.

---

### Post by nm_geo on 2012-04-02
> **uRock said:**
> I was trying to create the installer with persistance. That may have been the issue. I have faith in the cli you gave me getting the job done.

Great hope to hear good things... Out

---

### Post by jerrylamos on 2012-04-03
All my test systems, even the older 20 GB hard drive systems, have a ubuntu running on them.  So there's a grub2 available.

Grub2 will boot a .iso file directly from the hard drive, or even a .iso just copied onto a USB stick. No USB creator required.

Here's a sample /etc/grub.d/40_custom file that boots iso:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin ISO sda1" {
set isofile="/iso/precise-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```

A couple other steps:
sudo chmod 777 40_custom
sudo update-grub

Now if you want to do an install from the live environment, just do a 
sudo umount -r -l /dev/sda1
and away you go.

So I zsync the .iso, boot it off the hard drive, if I want to do an install in my case on this development forum onto a partition prepared by gparted.

Easy to repeat when some .iso change comes up.

Enjoy

Jerry

p.s. if you want to boot from the usb stick just change the (hd0,1) to whatever example (hd2,1) for a usb of /dev/sdc and the isofile to wherever you put the .iso.

---

