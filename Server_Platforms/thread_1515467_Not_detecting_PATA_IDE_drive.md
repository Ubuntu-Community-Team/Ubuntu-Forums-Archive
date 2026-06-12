---
title: "Not detecting PATA IDE drive"
date: 2010-06-22
forum: Server Platforms
---

### Post by buzzone on 2010-06-22
Hello everyone!

I've got a big issue with my Intel SS-4200. This is a headless NAS device. Pretty much standard hardware.

According to ([http://ss4200.pbworks.com/](http://ss4200.pbworks.com/)) it features two disk controllers:

> 
SiI 3132 SATA300 controller drives eSATA ports
Intel ICH7R controller drives 4 internal SATA ports and PATA port


The device has four internal SATA connector + one PATA connector on the board. I connected a 160GB 2.5" IDE device to the one PATA connector (using a 3.5" to 2.5" IDE adapter). On the SATA connectors there are no disks for now.

I use a minimal netboot Ubuntu install from a USB key to boot into the installer environment (using a serial console). 

In the bios (AMIBIOS) I can configure the disk controller to either Enhanced or Compatible.

Using Enhanced mode: I have six disk slots on the controller (the 4 SATA + 2 PATA). It's even possible to change the order (SATA first vs. PATA first). Depending on this setting the bios detects my PATA drive as master device either on "Primary IDE Master" or "Third IDE Master". Either way the Ubuntu kernel is not able to detect the PATA drive (fdisk -l or the installer partitioner).

Setting the disk controller to Compatible makes Ubuntu detect the PATA drive. But the big downside is that in this mode the bios allows for 2 ide channels only! That means I can only use 2 out of 4 SATA drives (because one ide channel is already used for PATA). But I need to connect 4 SATA drives. Using this mode I was able to install Ubuntu.

Then I was able to boot the Debian Lenny minimal install disk using the same technique (fromn usb key, serial console). Debian detects the PATA drive in both Enhanced and Compatible mode. Debian doesn't yet use libata but the older Linux IDE driver (PATA drive show up as /dev/hdx instead of /dev/sdx). But using Debian is no option for me (as they will also some time switch to libata this wouldn't be a solution anyway).

I am kind of stuck with this problem and don't get any further. There must be a way of having Ubuntu detect my PATA drive!

I will be extremely grateful for any hint!

Cheerio...
buzz


PS: I did a pretty exhaustive search before posting both on this forum and also using Google. For example here the issue is also described: [http://ss4200.pbworks.com/Ubuntu-server--9_10-amd64](http://ss4200.pbworks.com/Ubuntu-server--9_10-amd64) (under known issues)

A lot of discussions about similar issues suggest IDE cable problems. I checked my cable a dozen times. It is a brand new UDMA-133 80-pin cable and I am not using it the wrong way.

The IDE drive is jumpered as Master.


EDIT:
Here the issue is described (without an obvious solution):
[https://bugzilla.redhat.com/show_bug.cgi?id=503274](https://bugzilla.redhat.com/show_bug.cgi?id=503274)
[http://www.spinics.net/lists/linux-ide/msg35211.html](http://www.spinics.net/lists/linux-ide/msg35211.html)
[http://ubuntuforums.org/showthread.php?t=968795](http://ubuntuforums.org/showthread.php?t=968795)

---

