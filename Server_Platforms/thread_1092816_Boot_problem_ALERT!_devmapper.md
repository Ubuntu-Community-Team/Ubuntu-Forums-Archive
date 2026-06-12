---
title: "Boot problem ALERT! /dev/mapper"
date: 2009-03-10
forum: Server Platforms
---

### Post by bmcguire on 2009-03-10
First thing, this is my first installation of Ubuntu, so be gentle.

New installation of Ubuntu Server 8.10 on Intel Server with embedded raid controller.

Two 80 Gb drives raid 1 for the Ubuntu.

The installation appears to be successful.

At boot I get the following:
Gave up waiting for root device. Common problems:
-Boot args (cat /proc/cmdline)
 - check rootdelay=
 - check root=
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/ddf1_4c........(numbers/letters) does not exist. Dropping to a shell!

(initramfs)


I am assuming that it can't find the root (or boot) drive.

Please guide me oh wise Ubuntu Gods.

-A bit more info

If I type exit at the (initramfs) prompt the system finishes the boot.

Thanks

(Also if you ask for any files or output I will need directions)

---

### Post by bmcguire on 2009-03-11
Could not get anything to work. Searched threads, tried several things. No response to this thread so I went another route.

What I did was follow the instruction on this page [http://kuparinen.org/martti/comp/ubuntu/en/raid.html](http://kuparinen.org/martti/comp/ubuntu/en/raid.html). I setup a Software RAID configuration. Used the Alternate Installation CD.


Works fine, I have even already installed Axigen mail server.

---

