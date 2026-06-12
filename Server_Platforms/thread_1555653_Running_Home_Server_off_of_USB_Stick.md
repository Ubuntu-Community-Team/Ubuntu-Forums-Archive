---
title: "Running Home Server off of USB Stick"
date: 2010-08-18
forum: Server Platforms
---

### Post by mattlach on 2010-08-18
Hey all,

I was hoping for your opinion on this.

I intend to set up a home server using Ubuntu Server Edition , primarily for SMB NAS purposes, but it will also perform some other server duties like a media server (some transcoding may be necessary) and hosting a small FTP server over SSH.

The box will be as follows:
Dual core Athlon 64 1.5ghz with 2GB RAM
Direct USB 2.0 Connection to a 4 bay DROBO unit containing 4 drives in dual drive redundancy mode.

Will I hurt the performance of the system by booting and running it off of a USB stick?  Booting off of the DROBO is not ideal and I'd rather not have a hard drive spinning in it unless I have to (I'd put the hard drive in the DROBO instead).  I don't feel like spending money even on a low end 30Gig SSD.

Please let me know what your thoughts are!

Thanks,
Matt

---

### Post by surfer on 2010-08-18
as far as i know it is less the performance that you hurt but the usb stick. flash dirves have a limited number of writes they support. and a running server will write quite a lot on its disk.

---

### Post by stlsaint on 2010-08-18
I would say that you may have issues with running off usb due to the many writes to the usb disk. A thumb drive was not made to handle a servers load. Yes starting off on a usb will work for getting your server up and running for some time. But down the line you will want to look into getting another form of storage.

---

### Post by FuturePilot on 2010-08-18
A good way to kill a flash drive very quickly. ;)

---

### Post by mattlach on 2010-08-18
> **stlsaint said:**
> I would say that you may have issues with running off usb due to the many writes to the usb disk. A thumb drive was not made to handle a servers load. Yes starting off on a usb will work for getting your server up and running for some time. But down the line you will want to look into getting another form of storage.

Thanks for the feedback on this.

Will the server really have a lot of write cycles to the root filesystem?

I figured that after it is all set up, with everything installed, there will be some logs written in /var and some software updates, but otherwise all of the data will be written to the external redundant hard drive array. I would expect most of the operating system drive to be mostly reads and few writes.

I guess there might be more server writes than I thought.

---

### Post by FuturePilot on 2010-08-18
> **mattlach said:**
> Thanks for the feedback on this.

Will the server really have a lot of write cycles to the root filesystem?

I figured that after it is all set up, with everything installed, there will be some logs written in /var and some software updates, but otherwise all of the data will be written to the external redundant hard drive array. I would expect most of the operating system drive to be mostly reads and few writes.

I guess there might be more server writes than I thought.

Journaled file systems are very frequently making commits to the journal. This will definitely cause a lot of wear on a flash drive.

---

### Post by mattlach on 2010-08-18
> **FuturePilot said:**
> Journaled file systems are very frequently making commits to the journal. This will definitely cause a lot of wear on a flash drive.

Interesting.  Would it help to run ext2?  Will server performance or reliability suffer at all by running ext2 on th eboot drive?

---

### Post by mattlach on 2010-08-18
Maybe one of these [$39.99, 8GB Supertalent SSD's](http://www.ewiz.com/detail.php?p=FTM8GL25V&c=pw&hash=d529x5mWM%2ByeOljVIkx6UhqBU7xS2NAeaFMggC%2BPBA%2Fn8TJeWGApUfX9g3NYygbdzPULzTUkeS2e2ygn2f%2BSeUEPCKVTF6X3weRaqvtC6iQUc2qcvhf%2B7I7oaw) coupled with a non-journaling ext2 install for the operating system and boot partition will do the trick.

The redundant array will be on traditional hard drives, running ext3.

---

