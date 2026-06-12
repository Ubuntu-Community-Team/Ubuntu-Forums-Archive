---
title: "How to resize LVM swap partitiion?"
date: 2008-02-08
forum: System76 Support
---

### Post by UbuAgon on 2008-02-08
I installed 4GB RAM in my System76 serp3. I would like to increase my swap partition to 8GB.

I tried:

b@ubuntu:~$ lvextend -L8G /dev/mapper/ubuntu-swap_1
  /var/lock/lvm/V_mapper: open failed: Permission denied
  Can't get lock for mapper

How do I do this?

I'm using Ubuntu 7.10, Linux kernel 2.6.22-14-generic.

Also, can someone at System76 answer this question below?

I gather I need to install 64 bit to see more than 3 GB. My serp 3 was purchased in Dec, 2007. Is this recent enough that the 64 bit installation should not be a problem?

---

### Post by beuno on 2008-02-08
I suppose you already unmounted it and are executing it as root?

---

### Post by jdb on 2008-02-09
I don't like that LVM partition, you can't even mount it with a live CD.
At least not any I could find.

The first thing I did when I got mine was to reformat the disk as all ext3 partitions.
That will completely wipe out everything so be sure you understand the whole process before you start.

You have to back up all your data first and be sure to have a live Ubuntu CD.
If you haven't put much on the disk yet, it's a great opportunity to test your backup method.
If you do have a lot of stuff on the disk, it's kind of scary :)
Also you need a wideband connection to the internet for the Ubuntu updates and to load the System76 drivers.

I'm not sure WIFI works before you load the System76 drivers.
Just in case, I would make sure an ethernet cable connection is available.
It might work with just the Ubuntu drivers, but I'm not sure.

John Bowman

---

### Post by UbuAgon on 2008-02-09
> **beuno said:**
> I suppose you already unmounted it and are executing it as root?

With the caveat that I am basically feeling around in the dark, I attempted to infer what to do.

So this is my attempt to unmount the partition:
b@ubuntu:~$ umount /dev/mapper/ubuntu-swap_1
umount: /dev/mapper/ubuntu-swap_1 is not mounted (according to mtab)

Ok, so even if I didn't unmount it, it's now unmounted?

So then I tried executing lvextend as root:

b@ubuntu:~$ sudo lvextend -L8G /dev/mapper/ubuntu-swap_1
[sudo] password for b:
  Volume group mapper doesn't exist

/dev/mapper/ubuntu-swap_1 is what GParted calls the swap partition.

---

### Post by thomasaaron on 2008-02-11
I've not had any luck with re-sizing LVM partitions.

You might just want to try re-installing 64-bit ubuntu on your serp3 without LVM partitioning.

---

### Post by UbuAgon on 2008-02-14
> **thomasaaron said:**
> I've not had any luck with re-sizing LVM partitions.

You might just want to try re-installing 64-bit ubuntu on your serp3 without LVM partitioning.


Thanks. that's what I'll do.

---

### Post by bigredradio on 2008-02-14
Noooooooooooooooo! Don't get rid of LVM. This is just a matter of the command you are running. First, the device is being managed by device mapper so in a DF command is shows up as /dev/mapper. You need to run the same command, but reference the proper device name.

Also, you cannot 'mount' the swap device. You can use the command swapoff to 
temporarily disable the device from being used as swap. Then use swapon once you have finished resizing it.

/dev/[volume-group]/[logical-volume].

So in this case to find out the name of the volume group use the command:

# /sbin/vgdisplay 

Then use the same command you did earlier, but reference the proper device.

# lvextend -L8G /dev/[volumegroup]/ubuntu-swap_1

---

### Post by bigredradio on 2008-02-14
BTW, The old method of creating a swap device x2 the size of your physical ram is not necessary. Swap space is used when you "run out" of memory. If you have 4gb of memory, do you think you will run out to the point you will need 8 more gb or memory? If I start running out of ram, most likely 1 or 2 gb would be sufficient to handle any overages. Unless you are really using processes that use that much memory or creating "in memory" filesystems.

Back in the day when ram was small and expensive, using a swap device x2 the size was a good idea. But today, ram is cheap and large.

---

### Post by UbuAgon on 2008-02-23
> **bigredradio said:**
> 
So in this case to find out the name of the volume group use the command:

# /sbin/vgdisplay 


This command returned:

$ /sbin/vgdisplay
  No volume groups found

However,

> **bigredradio said:**
> BTW, The old method of creating a swap device x2 the size of your physical ram is not necessary. If you have 4gb of memory, do you think you will run out to the point you will need 8 more gb or memory? 

Point well taken. I think I'll quit worrying about the swap file size.

Thanks for the insight.

---

