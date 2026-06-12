---
title: "Truecrypt Automount Questions"
date: 2010-12-15
forum: Security
---

### Post by ryu kun on 2010-12-15
Hi!

I have two questions regarding auto mount function of Truecrypt.
[B]
First question:[/B]

I want to automatically mount my flash drive encrypted by Truecrypt using a keyfile whenever I plug the drive. How can I do this? I use Ubuntu 10.10.

**Second question:**

As I do not know the answer of my first question, I currently use following command in a startup script to mount my encrypted flash drive automatically at every system start-up.
> 
/usr/bin/truecrypt -k ~/keyfile --auto-mount=favorites

My problem with this method is, Truecrypt always search for the drive in the same path saved in favorite drives list, e.g. /dev/sdb1. However sometimes there are more than one flash drive plugged to my computer and my encrypted drive's path changes. In such cases Truecrypt cannot mount my encrypted drive because it cannot find the drive in its path. 

As a workaround I tried "auto-mount=devices" parameter. It is slow because it checks every mounted drive, and some of them external hard disk big in size. Moreover it does not recognize any mount point parameter. I'd like to mount the drive to the same mount point every time.
> 
/usr/bin/truecrypt -t --auto-mount=devices -p "" -k ~/keyfile /media/MyMountPoint

The command above mounts the drive however it is slow and to the destination of "/media/treucrypt1".

Any suggestions, please?

---

### Post by Robert S on 2010-12-15
Without going into a lot of detail - you can use udev - see [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html").  Unfortunately some of this is a bit out of date.  You can use udev rules to create consistent device names (eg /dev/my_pendrive) and also to automount devices using truecrypt or any other method.

---

### Post by ryu kun on 2010-12-25
> **Robert S said:**
> Without going into a lot of detail - you can use udev - see [http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html").  Unfortunately some of this is a bit out of date.  You can use udev rules to create consistent device names (eg /dev/my_pendrive) and also to automount devices using truecrypt or any other method.

Thank you for guiding me into the right direction. 

The link you gave me is my primary source to learn about udev. However I needed to make a further search for more current documentation, especially for Ubuntu. I reached following useful links:

[LIST]
[*][Create your own udev rules to control removable devices @ Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=168221)
[*][Connect your devices with udev @ Linux Wiki](http://www.linuxformat.co.uk/wiki/index.php/Connect_your_devices_with_udev)
[*][The new udev in Lucid @ shallowsky](http://shallowsky.com/blog/linux/kernel/lucid-udev.html) *(useful to learn about changes related to udev on Lucid)*
[*][Run a script on USB drive insertion @ Ubuntu Forums](http://ubuntuforums.org/showpost.php?p=1578267&postcount=22) *(same subject but from 2006 - I get fstab error (device not ready) when I follow the instructions here)*
[*][HowTo: Persistent drive symlinks at boot with udev rules @ Ubuntu Forums](http://newyork.ubuntuforums.org/showthread.php?t=1626172)
[/LIST]

I did the following using the information I got from above links:

[SIZE="3"]1. dmesg output[/SIZE]
I got the output of "dmesg" after I plugged in the drive, which is:

```
[ 1978.872064] usb 2-2: new high speed USB device using ehci_hcd and address 5
[ 1979.011756] scsi9 : usb-storage 2-2:1.0
[ 1980.009401] scsi 9:0:0:0: Direct-Access     Sony     Storage Media    1.00 PQ: 0 ANSI: 2
[ 1980.010352] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 1980.015617] sd 9:0:0:0: [sdb] 15663104 512-byte logical blocks: (8.01 GB/7.46 GiB)
[ 1980.016227] sd 9:0:0:0: [sdb] Write Protect is off
[ 1980.016235] sd 9:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 1980.016241] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1980.018758] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1980.018770]  sdb: sdb1
[ 1980.244063] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 1980.244072] sd 9:0:0:0: [sdb] Attached SCSI removable disk

```

[SIZE="3"]2. Get information about drive[/SIZE]
Then I used this command to find out what values can I use to identify my drive to udev.

```
udevadm info -a -p $(udevadm info -q path -n /dev/sdb1)
```

Please click **_[here]("http://paste.ubuntu.com/547492/")_** to see the output.

[SIZE="3"]3. Write the rule[/SIZE]
Then I wrote following udev rule:

```
ACTION=="add", KERNEL=="sd[b-g]", SUBSYSTEM=="usb", ATTRS{idVendor}=="054c", ATTRS{idProduct}=="0243", SYMLINK+="usb/Sony8GB", RUN+="/home/ryukun/Sabit/Scripts/test.sh", OPTIONS+="all_partitions,last_rule"
```

and put it into /etc/udev/rules.d/ directory and renamed it as "Sony8Gb.auto.rules" and I tried "85-Sony8Gb.auto.rules" as file name too.

I entered "udevadm trigger" but it did not create any symlink nor launched any script. I tried to restart the computer and plug the drive out and in, but nothing happened.

It did not work... :(

I made many try. I tried to use "scsi" for subsystem and various "ATTRS" values from the same scsi block but it did not help. After each change in the rule I rebooted the system as I could not trust "udevadm test" command. However it did not work.

I spent lots of hours on this and got frustrated.

I would greatly appreciate if anybody can help me.

---

### Post by deconstrained on 2011-02-22
As I mentioned via personal message: 

First, use the info that udevadm gives you about the device's tree. Find which item in the chain corresponds to the device itself, and then select key=value pairs from only that entry, and its "parent" device (the device listed just below it). In identifying a device *you can only use identifiers from the device itself and its parent device.* It's set up this way for a reason - to avoid ambiguity.

Next, the key=value pairs must actually reflect those that udevadm prints out when examining the device. 

If the device you want to examine or specify is /dev/sda for instance, look for [color=red]KERNEL=="sda"[/color] in the output of udevadm info and then go from there.

---

