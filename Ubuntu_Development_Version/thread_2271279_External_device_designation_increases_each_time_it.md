---
title: "External device designation increases each time it's mounted"
date: 2015-03-28
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2015-03-28
Stumbled upon an oddity. The first time I inserted and mounted this flash drive it showed up as /dev/sdc as it should since sda and sdb are internal drives, but then I noticed after ejecting it and plugging it back in again later the drive designation increases each time - up to /dev/sde now:

```
lance@lance-desktop:~$ sudo parted -l
[sudo] password for lance: 
Model: ATA WDC WD5000AAKS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  116GB  116GB   primary   ext4            boot
 2      116GB   232GB  116GB   primary   ext4
 4      232GB   500GB  268GB   extended
 6      232GB   252GB  20.5GB  logical   ext4
 7      252GB   273GB  20.4GB  logical   ext4
 8      273GB   293GB  20.4GB  logical   ext4
 9      293GB   313GB  20.4GB  logical   ext4
10      313GB   334GB  20.4GB  logical   ext4
11      334GB   354GB  20.4GB  logical   ext4
12      354GB   375GB  20.4GB  logical   ext4
13      375GB   395GB  20.4GB  logical   ext4
14      395GB   415GB  20.4GB  logical   ext4
15      415GB   436GB  20.4GB  logical   ext4
16      436GB   456GB  20.4GB  logical   ext4
17      456GB   477GB  20.4GB  logical   ext4
18      477GB   498GB  21.0GB  logical   ext4
 5      498GB   500GB  2517MB  logical   linux-swap(v1)


Model: ATA WDC WD800BB-63JK (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags


Model: SMI USB DISK (scsi)
**[COLOR="#FF0000"]Disk /dev/sde: 3995MB[/COLOR]**
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3995MB  3994MB  primary  fat32        lba

```

What package do think a bug should be filed against?

---

### Post by dino99 on 2015-03-29
when the drive is ejected, then plugged back, i suppose you mean within the same session , right ?
If it is the case , then with multiple eject/plug, this seems expected to get a new mount address as the device is not really identified (its only, each time, a new device).
This is not of course a very clean process, but if the system was able to identify a device then reaffecting the same mount ID when plugged back, how it should not be confused by the user unplugging/plugging back multiple devices with the same make/model ? It simply cant without also knowing some more settings like identifying the data/free space/...
Well simply to complicated. So the actual increasing within the same session seem expected to me.

---

### Post by mc4man on 2015-03-29
It wouldn't be expected behavior to me, nor anything I've seen prior to 15.04. As I don't currently have any 15.04 installs can't comment further other than - Does this also happen with the latest Ubuntu 15.04 image install or just UbuntuGnome?

---

### Post by QDR06VV9 on 2015-03-29
Running Mate Session only I can confirm same behavior.
Will try to if I remember to get some screenshots of the oddities.

---

### Post by kansasnoob on 2015-03-29
> **mc4man said:**
> It wouldn't be expected behavior to me, nor anything I've seen prior to 15.04. As I don't currently have any 15.04 installs can't comment further other than - Does this also happen with the latest Ubuntu 15.04 image install or just UbuntuGnome?

Good question, I had to check and no, it's not effecting Ubuntu Vivid, only Ubuntu GNOME so far as I personally know ................ but I see another comment indicating Ubuntu MATE is also effected.

This just struck me as odd. I had two machines running at the time, the first to create live USB drives for testing, and the second to perform the actual tests. So I'd create a Vivid live USB drive using this install of Vivid, then after checking the results I'd plug that drive back into PC #1 and create a Utopic live USB, and finally a Trusty live USB.

I've done this sort of thing quite a bit down thru the years .............. rinse-n-repeat creating different flavors, or in this case different versions, with the same OS and I'd never seen this happen before. Not a huge deal since I was using usb-creator but if someone were using dd it'd make them pay attention ;)

---

### Post by Elfy on 2015-03-29
just tried in xubuntu, mounted, unmounted, ejected 3 times - same each time sdd

---

### Post by mc4man on 2015-03-29
> **kansasnoob said:**
> Good question, I had to check and no, it's not effecting Ubuntu Vivid, only Ubuntu GNOME so far as I personally know ................ but I see another comment indicating Ubuntu MATE is also effected.

This just struck me as odd. I had two machines running at the time, the first to create live USB drives for testing, and the second to perform the actual tests. So I'd create a Vivid live USB drive using this install of Vivid, then after checking the results I'd plug that drive back into PC #1 and create a Utopic live USB, and finally a Trusty live USB.

I've done this sort of thing quite a bit down thru the years .............. rinse-n-repeat creating different flavors, or in this case different versions, with the same OS and I'd never seen this happen before. Not a huge deal since I was using usb-creator but if someone were using dd it'd make them pay attention ;)

Then it seems like something that should be addressed, what source to bug I'm not sure.
What would happen when you used up the alphabet, like what's after sdz?

---

### Post by sammiev on 2015-03-29
I have done a fresh install today of Ubuntu-gnome Vivid and I'm not having the OP troubles. ( Tried 5 different USB sticks twice and all reported /dev/sdb, one behind the other )  Wished I would have tried it before the fresh install.

---

### Post by ventrical on 2015-03-29
All well on ubuntu-unity.

Regards..

---

### Post by kansasnoob on 2015-03-29
This install is getting long in the tooth - installed around Alpha 1, so it could be that I've tweaked something in that period of time that I can't even remember. I'll try a fresh install ands see what happens.

---

### Post by kansasnoob on 2015-03-29
OK, I may have discovered the culprit. I was having trouble even reproducing this behavior on the same Ubuntu GNOME Vivid install ................ it turns out that just mounting, unmounting, and removing the USB drive does NOT trigger this behavior. 

**[COLOR="#FF0000"]Only using usb-creator appears to cause this[/COLOR]** :idea:

So maybe it's a usb-creator bug??? This will require quite a bit of rinse-n-repeat testing to see what versions and/or flavors are effected. To be perfectly honest I've really never cared for usb-creator, particularly since it asks for admin rights to install bootloader late in the process (and fails if you don't notice it fairly quickly) but I've been testing it just to see if known bugs are getting fixed.

---

### Post by mc4man on 2015-03-29
Even though it's always got at least one ongoing issue, if not more,  I still use s-d-c, just need to know what's wrong & adjust. (like I never let it format the drive.
unetbottin is ok but it sometimes it's creations don't boot up. Also, at least last I checked, it has DnD active when browsing for image which has caught me a couple of times.
(- haven't checked in a while on that..

---

### Post by kansasnoob on 2015-03-29
Well, I'd kept getting failures creating a live USB with Vivid and had been trying over & over again. this is the failure to install bootloader (it's persistent as can be):

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1338528](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1338528)

Among other things I was trying to test the fix for this bug:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)

But I'm done beating my head against the wall with this issue ATM. I'll give it another look in a few days. BTW it also effects the version of usb-creator in utopic-proposed.

---

### Post by ventrical on 2015-03-30
> **kansasnoob said:**
> This install is getting long in the tooth - installed around Alpha 1, so it could be that I've tweaked something in that period of time that I can't even remember. I'll try a fresh install ands see what happens.

:)

[http://ubuntuforums.org/showthread.php?t=1901896&highlight=nursing+multiple+installs](http://ubuntuforums.org/showthread.php?t=1901896&highlight=nursing+multiple+installs)

---

### Post by mc4man on 2015-03-30
Finally decided to see what the DnD with root permissions in unetbootin was about via a bug - 
[https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/1438236](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/1438236)
[https://github.com/gkovacs/unetbootin/issues/19](https://github.com/gkovacs/unetbootin/issues/19)

---

### Post by kansasnoob on 2015-03-30
> **mc4man said:**
> Finally decided to see what the DnD with root permissions in unetbootin was about via a bug - 
[https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/1438236](https://bugs.launchpad.net/ubuntu/+source/unetbootin/+bug/1438236)
[https://github.com/gkovacs/unetbootin/issues/19](https://github.com/gkovacs/unetbootin/issues/19)

I subscribed to the launchpad bug report. It seems like 90% of what I try to do in Vivid ATM fails, at least to some degree, so I'm going to give it a rest for a few days until the dust (and my nerves) settles.

---

### Post by Hazzabin on 2015-03-30
[COLOR=#000000]mc4man wrote 'still use s-d-c' what is that[/COLOR]

---

### Post by mc4man on 2015-03-30
> **Hazzabin said:**
> [COLOR=#000000]mc4man wrote 'still use s-d-c' what is that[/COLOR]

s-d-c = startup disc creator (usb-creator-gtk package

---

### Post by Hazzabin on 2015-03-30
Thank you mc4man

---

### Post by mc4man on 2015-03-30
It seems to be ok on a live session, maybe it's not that it can't install the bootloader but a permission deal.
You could try this - 
```
sudo nano /var/lib/polkit-1/localauthority/50-local.d/sdc.pkla
```
c&p this into nano, then save (ctrl+o enter ctrl+x

```
[Install bootloader]
Identity=unix-group:sudo
Action=com.ubuntu.usbcreator.bootloader
ResultActive=yes
```
Then try to make a usb but 1st. fresh  format the drive to FAT in Disks or gparted, never in s-d-c. Also wait till s-d-c lets you pick Discarded on ... option, can take several sec's or more..

---

### Post by kansasnoob on 2015-04-02
> **ventrical said:**
> :)

[http://ubuntuforums.org/showthread.php?t=1901896&highlight=nursing+multiple+installs](http://ubuntuforums.org/showthread.php?t=1901896&highlight=nursing+multiple+installs)

That was exactly the case here :oops:

I'd been fiddling around trying to troubleshoot this bug that's been around since at least 13.04:

[https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1069964)

I'd tried this workaround:

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071739/comments/6](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1071739/comments/6)

But that caused problems with USB and camera mounting so I tried installing 'usbmount' and 'pmount'.

**[COLOR="#FF0000"]Don't try that![/COLOR]** Simply purging them does NOT fix this mount point changing issue so I had to reinstall.

Anyway I've tried reproducing this with unmolested installs of Ubuntu, Ubuntu GNOME, and Ubuntu Mate to no avail, so chalk this one up to my own fiddling.

---

### Post by ventrical on 2015-04-02
I had just seen a reminder in another thread about <nomodeset>  from Cariboo907...hmmm..?

and this ..

[http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)

which was an interesting read from times past.  I wonder how all this is still applying now...one way to find out eh :)

---

