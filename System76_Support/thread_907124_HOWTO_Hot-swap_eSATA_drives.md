---
title: "HOWTO: Hot-swap eSATA drives"
date: 2008-09-01
forum: System76 Support
---

### Post by Emblem Parade on 2008-09-01
A very useful feature of my recently purchased Pangolin Performance laptop from system76 is that it has an eSATA port, allowing for very fast external drives.

The eSATA standard supports hot-swapping of drives, but Ubuntu 8.04 doesn't know how to do this automatically.

You can do this manually by installing scsiadd:

```
sudo aptitude install scsiadd
```

Before swapping, be sure to unmount the partitions on the external drive. Then, plug in the new drive. The command to re-scan eSATA is:

```
sudo scsiadd -s 3
```

Where "3" is the appropriate "SCSI channel," which may differ per your machine. There's no harm in scanning other channels, so don't worry about experimenting.

Once the new drive is detected, the rest of Ubuntu will react accordingly: the Linux kernel will recognize it, and GNOME's Nautilus file manager will show the partitions as mountable.

*IMPORTANT: Sometimes, especially if there is no drive connected, the command can take several minutes to complete. It might look like it's hanging, but it's not. Be patient, and all will be well.*

Hopefully this will all happen automatically in the next version of Ubtuntu.

By the way, if you'd like to install Windows on an external hard drive, check out my guide [here]("http://ubuntuforums.org/showthread.php?p=5696516").

---

### Post by thomasaaron on 2008-09-01
Thank you for the tutorial.

---

### Post by bates on 2008-09-27
Do I need to have the drive partitioned first to use this? Just bought a Seagate 1TB drive and Thermaltake Vi-On e-sata case and hardy is just sitting there doin nuthin.

How many channels are there? I've tried a few and they all give me the same 2 drives (my internal and my dvd-r).

Also, I am running 64 bit hardy.

---

### Post by jdb on 2008-09-28
> **bates said:**
> Do I need to have the drive partitioned first to use this? Just bought a Seagate 1TB drive and Thermaltake Vi-On e-sata case and hardy is just sitting there doin nuthin.

How many channels are there? I've tried a few and they all give me the same 2 drives (my internal and my dvd-r).

Also, I am running 64 bit hardy.

I'm just guessing, but this is what I'd try.

Open a terminal and with the drive unplugged run this command:

ls  -lrt   /dev

It will list all devices in the order they were created, just note the last few.

Plug in your drive and again run:

ls  -lrt   /dev

There should be a couple new devices among the last few, probably sdb & sdb1.

If there is not a new device with a number after it (like sdb1) then you will have to partition the drive before you go any further.
gparted is a good graphical tool for partitioning drives.
If there is a new device with a number after it, then you can mount it:

sudo  mount   /dev/sdb1   /mnt

I used sdb1 in the example, you should used whatever dev you got from the ls.
/mnt is just a convenient directory to mount things on.
You can mount it on any directory you want, but the contents of that directory will not be accessible while it is mounted, it is best to use an empty directory.
You can make a directory as follows:

sudo  mkdir  /newdrive

Once it's mounted, you should be able to read & write it by reading & writing the directory it is mounted on.

To automatically mount it every time you boot add this line to /etc/fstab:

/dev/sdb1   /newdrive          ext3    relatime        0       2

This assumes that it was partitioned as an ext3 file system.
Also, instead of "newdrive", supply the directory you want it mounted on.

If you want to unplug it, first run:

sync

Then run:

umount /dev/sdb1

  or

umount /newdrive


jdb

---

### Post by Emblem Parade on 2008-09-29
You should not have to partition the disk in order for this method to work. Although, until you partition the disk, it will not appear in the filesystem -- not in GNOME, Nautilus, etc.

I think the best way to check what drives are connected, partitioned or not, is to use this command:

```
sudo fdisk -l
```

It will show you all physical drives and what partitions, if any, are in them. This will work fine even with a SATA/eSATA connected drive -- assuming you get the SCSI system to recognize it.

You also asked how many channels there are -- I'm afraid I don't know! The documentation is pretty spotty on this. I hope Ubuntu improves support for eSATA in the future. Many new laptops have an eSATA port these days.

---

### Post by gnugu on 2008-11-06
Hi,
I am able to discover my eSATA drive with scsiadd -s X.

The problem I'm having is that the channel number keeps changing on me. This is no good, because I want to write a script that will discover and mount the drive.

Is it possible to scan a range of channels?
How do I find out how many channels I have?

Running just scsiadd -s without any number doesn't do anything for me.

Thanks.

---

### Post by scarf on 2008-11-29
i don't think my drive is even showing up.  i had tried scsiadd -s and it doesn't list the new esata enclosure i plugged in.  ls -lrt doesn't change after plugging in and turning on the enclosure.  i had tried fdisk -l and it isn't showing and extra disks detected.  i tried rebooting the system and repeating above commands.  i am plugging it into an on-board esata plug on the back of the motherboard.  i checked the BIOS and there doesn't seem to be any setting for turning on and off esata.

is the motherboard faulty??

is there anything else i can check before coming to that conclusion?

---

### Post by gnugu on 2008-12-01
scarf,
I know that Windows recognizes eSata drives. That's what I would try before dumping the mother board.

As for my quest, I gave up on eSATA for now and am using USB.

Some say that Ubuntu 8.10 should recognize eSATA. I can't confirm this because I can't get 8.10 working on my mother board at all.

---

### Post by scarf on 2008-12-01
you are lucky in that i have one of those windows bartpe cds.  i will give it a try and report back.  no way in hell i am putting any bits of windows on my hard disk... it will be bad enough having it in the ram... will have to run memtest afterwards to clear it all out ;)

it could be, that the hardware driver for the esata controller on this motherboard is not yet supported.  i will provide as many details as possible, perhaps a dmesg?

stay tuned.

---

### Post by drvk on 2008-12-21
> **gnugu said:**
> scarf,
I know that Windows recognizes eSata drives. That's what I would try before dumping the mother board.

As for my quest, I gave up on eSATA for now and am using USB.

Some say that Ubuntu 8.10 should recognize eSATA. I can't confirm this because I can't get 8.10 working on my mother board at all.

I confirm, but no auto-mount. Not on my system.
But if some-one has any idea I'll take it.
Last year on 7.10 I had auto mount on internal sata devices but since dbus it is not working any more.
Any hint is welcome.

---

### Post by xjgnsdof on 2009-09-05
Great guide. I can now hot swap SATA drives in my Thermaltake BlacX dock. Thanks.

---

### Post by HunterThomson on 2010-01-22
I'll be trying this tomorrow.Thanks for the HowTo :)

This an old thread but if anyone ells wants to "just make sure their eSATA port and external case works and stuff". On my laptop HP elitebook 8530w. It dose not hot swap by itself. However, if I plug in the eSATA drive then re-boot. It will find the drive on Boot. So, try that to make sure all the hardware works.

Also, it is my understanding that it is not a special SATA controller that controls the eSATA port. It's just your normal SATA controller. So, wile it still vary well could be a driver problem too. If true, this makes me think that it is less likely a SATA controller driver problem. Like from what I remember the motherboard just thinks it's another SATA drive and knows nothing about "eSATA".

---

### Post by webdevelopment4 on 2010-10-06
i have a kf-1000-bk hot swap unit for sata, does this work with ubuntu 10.04?  currently its not recognzing the drive pluged into it...

also the below command does not show the drive that is plugged into the hot swap unit...
sudo fdisk -l

---

