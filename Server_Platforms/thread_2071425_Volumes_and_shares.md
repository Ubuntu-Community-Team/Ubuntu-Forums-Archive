---
title: "Volumes and shares"
date: 2012-10-15
forum: Server Platforms
---

### Post by darthspringbok on 2012-10-15
I have Ubuntu server 12.04 set up and have installed it onto a USB stick. I am trying to set this up as a file and media storage/NAS. In the box I have 2x 160GB hard drives that I am trying to setup as a single volume (i.e. approx 320GB)
 
I have tried to do this through Webmin and can setup the volume but just cannot seem to mount it, therefore not available to SAMBA.
 
Can someone give me an idiot's guide to doing this through CLI or some instruction on getting webmin to do this?

---

### Post by darkod on 2012-10-15
First of all, for 2x160GB to give you usable 320GB that means raid0. You are aware that raid0 doesn't protect your data with any redundancy, right? If one disk goes, you lose it all.

Having said that, you can check the disk devices with:
sudo parted -l (small L)

Post the output here.

And decide how you want to call your mount point, for example /data, /storage, /media/storage, etc.

---

### Post by darthspringbok on 2012-10-15
> **darkod said:**
> First of all, for 2x160GB to give you usable 320GB that means raid0. You are aware that raid0 doesn't protect your data with any redundancy, right? If one disk goes, you lose it all.
 
Having said that, you can check the disk devices with:
sudo parted -l (small L)
 
Post the output here.
 
And decide how you want to call your mount point, for example /data, /storage, /media/storage, etc.
 
I understand that I will be using RAID0 as I have its intended content backed up elswhere. This is just a test box for setting up Ubuntu for learning.
 
I will get the output  you have asked for posted when I get in later.
 
For the naming I will be going for /share

---

### Post by bab1 on 2012-10-15
> **darthspringbok said:**
> I have Ubuntu server 12.04 set up and have installed it onto a USB stick. I am trying to set this up as a file and media storage/NAS. In the box I have 2x 160GB hard drives that I am trying to setup as a single volume (i.e. approx 320GB)
 
I have tried to do this through Webmin and can setup the volume but just cannot seem to mount it, therefore not available to SAMBA.
 
Can someone give me an idiot's guide to doing this through CLI or some instruction on getting webmin to do this?

I think you are referring to LVM for your disks.  See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.howtogeek.com/howto/36568/what-is-logical-volume-management-and-how-do-you-enable-it-in-ubuntu/") and [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/") for information.

---

### Post by LHammonds on 2012-10-15
Yes, LVM is what you will want to use.  In my sig, I have a step-by-step guide which covers setting up LVM on a production server and then adding more drives to increase volume space.

LHammonds

---

