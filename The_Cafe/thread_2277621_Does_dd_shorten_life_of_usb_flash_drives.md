---
title: "Does dd shorten life of usb flash drives ?"
date: 2015-05-10
forum: The Cafe
---

### Post by linuxyogi on 2015-05-10
Hi,
At the moment I have only one usb flash drive. Sometimes I use dd to write distro ISOs to it to install from usb.

When finished installing I run zero fill drive for some seconds to erase the boot sector and finally use Gparted

to create a partition table. I have done this quite a number of times. Now when I copy some video files to the 

flash drive and connect it to my XBMC rapberry pi its hanging and I have to hard reset it.

So does dd shorten life of drives ?

---

### Post by buzzingrobot on 2015-05-10
As far as I know, dd has no impact on the lifetime of a USB stick.  I use it all the time on a few pretty old sticks. They physically fall apart first.

If XMBC expects to see a file system on that USB stick, be sure there is one, and not just an empty partition.  (dd just moves bits from here to there, no filesystems involved. If  a stick has a filesystem on it and you use dd to burn an iso image on it, the filesystem is gone.)

---

### Post by tgalati4 on 2015-05-10
I would get some newer, faster USB sticks to use for video streaming.  There should be some log entries in /var/log/syslog on the RaspberryPi to determine what is failing.  The USB chipset on the RP is not great and perhaps not up to the bandwidth required to stream high-definition videos.  Disconnect your ethernet from the RP and see if performance improves.

---

### Post by sffvba[e0rt on 2015-05-10
Well it will add some reads and writes to the whole device but they can take plenty of those before they die.

---

### Post by linuxyogi on 2015-05-10
I used the check option of gparted to repair the partition. Now its working okay but I agree that this flash drive is a bit slow.

---

### Post by sudodus on 2015-05-10
> **not found said:**
> Well it will add some reads and writes to the whole device but they can take plenty of those before they die.
+1

But sometimes you can re-vitalize a pendrive by writing zeros to it, ***wiping*** it. ***mkusb*** uses ***dd*** under the hood, it 'wraps security around dd'. If a pendrive is partially locked, it might be released by  overwriting the system with zeros (at the level below file systems  and partitions).

Wipe the whole device with mkusb, and after  that use gparted to create a new partition table and after that a  partition with a file system.

See this link [https://help.ubuntu.com/community/mk...e_whole_device]("https://help.ubuntu.com/community/mkusb#Wipe_the_first_megabyte_or_the_whole_device")

['gridlock']("http://ubuntuforums.org/showthread.php?t=2178075&p=12805426#post12805426")  - If a pendrive starts running slower, it might soon get 'gridlocked',   and wiping might relieve the situation by releasing good memory cells. 

- When old pendrives get slower  (typically reduce the writing speed to  half), wiping the whole device  can recover the original (or near  original) write speed. See [this link about pendrive lifetime]("http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297").

---

### Post by linuxyogi on 2015-05-10
@sudodus
Thanks for the links.

---

### Post by HermanAB on 2015-05-10
Howdy,

Modern USB thingies have built-in controllers that shuffle blocks around automatically for wear leveling, so you need not worry about it.

---

