---
title: "SoftRAID 5 Always Failing"
date: 2011-03-17
forum: Server Platforms
---

### Post by dsmacman on 2011-03-17
Hello all,

I have a computer setup running the newest version of Ubuntu (10.10 I believe) and I have been trying to use 6 USB2.0, 2TB drives in a RAID5 for 10TB of storage.  

I use the gnome disc utility to configure them into a RAID, but after some amount of time (could be during first sync, or after a few days, but no longer than a week)  two of the RAID drives will just decide to drop out in quick succession.  That is, one will drop then the other within a couple minutes, I only know that because I watched it happen one time.  :)

So before I attempt to setup the RAID for the 8th time, I was curious to know if I was doing something wrong.. any ideas?

---

### Post by rubylaser on 2011-03-17
Have you looked at your logfiles to see why your drives are dropping out?
```
cat /var/log/syslog | grep disk
```
And, what does your /etc/mdadm/mdadm.conf file look like?
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by kenada on 2011-03-18
What type of drives are they?

---

### Post by dsmacman on 2011-03-19
Here is the results of  "cat /var/log/syslog | grep disk":

> Mar 16 20:56:52 (computerhostname) kernel: [253251.883359]  disk 0, o:1, dev:sdf1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883362]  disk 1, o:1, dev:sdg1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883364]  disk 2, o:1, dev:sdh1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883368]  disk 3, o:0, dev:sdb1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883371]  disk 4, o:1, dev:sde1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883374]  disk 5, o:1, dev:sdc1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883382]  disk 0, o:1, dev:sdf1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883384]  disk 1, o:1, dev:sdg1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883387]  disk 2, o:1, dev:sdh1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883390]  disk 4, o:1, dev:sde1
Mar 16 20:56:52 (computerhostname) kernel: [253251.883392]  disk 5, o:1, dev:sdc1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931902]  disk 0, o:1, dev:sdf1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931905]  disk 1, o:1, dev:sdg1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931909]  disk 2, o:1, dev:sdh1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931912]  disk 4, o:0, dev:sde1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931916]  disk 5, o:1, dev:sdc1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931924]  disk 0, o:1, dev:sdf1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931927]  disk 1, o:1, dev:sdg1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931930]  disk 2, o:1, dev:sdh1
Mar 16 22:19:27 (computerhostname) kernel: [258206.931933]  disk 5, o:1, dev:sdc1
Mar 16 23:39:56 (computerhostname) kernel: [263035.301189] sd 11:0:0:0: [sdd] Attached SCSI disk
Mar 16 23:40:11 (computerhostname) kernel: [263050.452191] sd 12:0:0:0: [sdi] Attached SCSI disk
Mar 16 23:48:14 (computerhostname) kernel: [263533.950276] sd 13:0:0:0: [sdj] Attached SCSI disk
Mar 16 23:48:18 (computerhostname) kernel: [263537.511626] sd 14:0:0:0: [sdk] Attached SCSI disk
Mar 16 23:50:36 (computerhostname) kernel: [    1.111818] PM: Resume from disk failed.
Mar 16 23:50:36 (computerhostname) kernel: [    2.229962] sd 3:0:0:0: [sda] Attached SCSI disk
Mar 16 23:49:04 (computerhostname) kernel: [   24.974152] sd 5:0:0:0: [sdc] Attached SCSI disk
Mar 16 23:49:04 (computerhostname) kernel: [   25.033734] sd 8:0:0:0: [sdf] Attached SCSI disk
Mar 16 23:49:04 (computerhostname) kernel: [   25.271067] sd 4:0:0:0: [sdb] Attached SCSI disk
Mar 16 23:49:05 (computerhostname) kernel: [   25.397160] sd 7:0:0:0: [sde] Attached SCSI disk
Mar 16 23:49:05 (computerhostname) kernel: [   25.488471] sd 6:0:0:0: [sdd] Attached SCSI disk
Mar 16 23:49:05 (computerhostname) kernel: [   25.582054] sd 9:0:0:0: [sdg] Attached SCSI disk
Mar 16 23:54:08 (computerhostname) kernel: [  328.976603] md/raid:md0: device sdf1 operational as raid disk 4
Mar 16 23:54:08 (computerhostname) kernel: [  328.976610] md/raid:md0: device sde1 operational as raid disk 3
Mar 16 23:54:08 (computerhostname) kernel: [  328.976614] md/raid:md0: device sdd1 operational as raid disk 2
Mar 16 23:54:08 (computerhostname) kernel: [  328.976618] md/raid:md0: device sdc1 operational as raid disk 1
Mar 16 23:54:08 (computerhostname) kernel: [  328.976621] md/raid:md0: device sdb1 operational as raid disk 0
Mar 16 23:54:08 (computerhostname) kernel: [  328.988113]  disk 0, o:1, dev:sdb1
Mar 16 23:54:08 (computerhostname) kernel: [  328.988117]  disk 1, o:1, dev:sdc1
Mar 16 23:54:08 (computerhostname) kernel: [  328.988120]  disk 2, o:1, dev:sdd1
Mar 16 23:54:08 (computerhostname) kernel: [  328.988123]  disk 3, o:1, dev:sde1
Mar 16 23:54:08 (computerhostname) kernel: [  328.988127]  disk 4, o:1, dev:sdf1
Mar 16 23:54:09 (computerhostname) kernel: [  329.368921] md0: bitmap initialized from disk: read 30/30 pages, set 953863 bits
Mar 16 23:54:09 (computerhostname) kernel: [  329.371705]  disk 0, o:1, dev:sdb1
Mar 16 23:54:09 (computerhostname) kernel: [  329.371709]  disk 1, o:1, dev:sdc1
Mar 16 23:54:09 (computerhostname) kernel: [  329.371713]  disk 2, o:1, dev:sdd1
Mar 16 23:54:09 (computerhostname) kernel: [  329.371716]  disk 3, o:1, dev:sde1
Mar 16 23:54:09 (computerhostname) kernel: [  329.371719]  disk 4, o:1, dev:sdf1
Mar 16 23:54:09 (computerhostname) kernel: [  329.371722]  disk 5, o:1, dev:sdg1
Mar 16 23:54:09 (computerhostname) kernel: [  329.379156] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Mar 16 23:56:09 (computerhostname) kernel: [  449.353455] sd 10:0:0:0: [sdh] Attached SCSI disk
Mar 16 23:56:45 (computerhostname) kernel: [  485.737015] sd 11:0:0:0: [sdh] Attached SCSI disk
Mar 17 08:48:45 (computerhostname) kernel: [32406.208230]  disk 0, o:1, dev:sdb1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208234]  disk 1, o:0, dev:sdc1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208237]  disk 2, o:1, dev:sdd1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208240]  disk 3, o:1, dev:sde1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208243]  disk 4, o:1, dev:sdf1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208246]  disk 5, o:1, dev:sdg1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208254]  disk 0, o:1, dev:sdb1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208257]  disk 1, o:0, dev:sdc1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208260]  disk 2, o:1, dev:sdd1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208262]  disk 3, o:1, dev:sde1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208265]  disk 4, o:1, dev:sdf1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208280]  disk 0, o:1, dev:sdb1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208283]  disk 1, o:0, dev:sdc1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208285]  disk 2, o:1, dev:sdd1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208288]  disk 3, o:1, dev:sde1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208290]  disk 4, o:1, dev:sdf1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208298]  disk 0, o:1, dev:sdb1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208300]  disk 2, o:1, dev:sdd1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208303]  disk 3, o:1, dev:sde1
Mar 17 08:48:45 (computerhostname) kernel: [32406.208306]  disk 4, o:1, dev:sdf1
Mar 17 20:50:36 (computerhostname) kernel: [75716.972541] sd 12:0:0:0: [sdi] Attached SCSI disk
Mar 17 20:50:41 (computerhostname) kernel: [75721.738904] sd 13:0:0:0: [sdj] Attached SCSI disk
Mar 17 21:02:17 (computerhostname) kernel: [76418.085927] md/raid:md0: device sdi operational as raid disk 4
Mar 17 21:02:17 (computerhostname) kernel: [76418.085934] md/raid:md0: device sdg operational as raid disk 3
Mar 17 21:02:17 (computerhostname) kernel: [76418.085938] md/raid:md0: device sdf operational as raid disk 2
Mar 17 21:02:17 (computerhostname) kernel: [76418.085941] md/raid:md0: device sde operational as raid disk 1
Mar 17 21:02:17 (computerhostname) kernel: [76418.085945] md/raid:md0: device sdb operational as raid disk 0
Mar 17 21:02:17 (computerhostname) kernel: [76418.102417]  disk 0, o:1, dev:sdb
Mar 17 21:02:17 (computerhostname) kernel: [76418.102421]  disk 1, o:1, dev:sde
Mar 17 21:02:17 (computerhostname) kernel: [76418.102424]  disk 2, o:1, dev:sdf
Mar 17 21:02:17 (computerhostname) kernel: [76418.102427]  disk 3, o:1, dev:sdg
Mar 17 21:02:17 (computerhostname) kernel: [76418.102430]  disk 4, o:1, dev:sdi
Mar 17 21:02:17 (computerhostname) kernel: [76418.107096]  disk 0, o:1, dev:sdb
Mar 17 21:02:17 (computerhostname) kernel: [76418.107099]  disk 1, o:1, dev:sde
Mar 17 21:02:17 (computerhostname) kernel: [76418.107103]  disk 2, o:1, dev:sdf
Mar 17 21:02:17 (computerhostname) kernel: [76418.107106]  disk 3, o:1, dev:sdg
Mar 17 21:02:17 (computerhostname) kernel: [76418.107109]  disk 4, o:1, dev:sdi
Mar 17 21:02:17 (computerhostname) kernel: [76418.107112]  disk 5, o:1, dev:sdj
Mar 17 21:02:17 (computerhostname) kernel: [76418.117125] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.


And then my mdadm.conf:

> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Mon, 07 Mar 2011 17:36:47 -0500
# by mkconf $Id$



The drives I'm using are 6- 2TB  Iomega drives (as seen here: [http://go.iomega.com/en-us/products/external-hard-drive-desktop/prestige-desktop-series/prestige-charcoal/](http://go.iomega.com/en-us/products/external-hard-drive-desktop/prestige-desktop-series/prestige-charcoal/))


Thank you for responding :)

---

### Post by disabledaccount on 2011-03-19
These are USB drives, so You should scan logs for USB errors:
>cat /var/log/kern.log | grep "usb" (or "usb-storage")

Watch for events where one of those disk is re-connected - I suppose this coud be the reason.

---

### Post by rubylaser on 2011-03-19
You need to add your array to your mdadm.conf file... This will help your situation a lot.  And, yes, I should have had you looking for USB devices in your syslog :)

```
echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
echo "HOMEHOST fileserver" >> /etc/mdadm/mdadm.conf
echo "MAILADDR root@localhost" >> /etc/mdadm/mdadm.conf
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

You're missing the ARRAY line which is really the most important part.  It will look something like this when it's done.
```
 
DEVICE partitions
HOMEHOST fileserver
MAILADDR root@localhost
ARRAY /dev/md0 metadata=0.90 UUID=d4e58776:640274d8:e368bf24:bd0fce41
```

---

### Post by Vegan on 2011-03-19
Get a controller card then you woes will go away.

Software RAID is begging for trouble.

---

### Post by dsmacman on 2011-03-19
After doing   cat /var/log/kern.log | grep "usb",   i have a whole lot of entries like these:

```
Mar 18 02:48:54 (computerhostname) kernel: [97215.120046] usb 1-1: reset high speed USB device using ehci_hcd and address 9
Mar 18 02:49:47 (computerhostname) kernel: [97268.176045] usb 1-1: reset high speed USB device using ehci_hcd and address 9
Mar 18 02:58:56 (computerhostname) kernel: [97817.168047] usb 1-1: reset high speed USB device using ehci_hcd and address 9

```

I also have a few disconnects and reconnects, but I'm not sure if that was an error or if it was me physically unplugging the drive and plugging it back in (the only way the drive pops back up in gnome's disk utility.

Then this:

```
Mar 16 20:56:53 (computerhostname) kernel: [253252.200106] usb 4-1: device descriptor read/64, error -71
Mar 16 20:56:53 (computerhostname) kernel: [253252.424214] usb 4-1: device descriptor read/64, error -71
Mar 16 20:56:53 (computerhostname) kernel: [253252.640055] usb 4-1: new full speed USB device using uhci_hcd and address 3
Mar 16 20:56:53 (computerhostname) kernel: [253252.760058] usb 4-1: device descriptor read/64, error -71
Mar 16 20:56:53 (computerhostname) kernel: [253252.992057] usb 4-1: device descriptor read/64, error -71
Mar 16 20:56:54 (computerhostname) kernel: [253253.208139] usb 4-1: new full speed USB device using uhci_hcd and address 4
Mar 16 20:56:54 (computerhostname) kernel: [253253.616038] usb 4-1: device not accepting address 4, error -71
Mar 16 20:56:54 (computerhostname) kernel: [253253.728046] usb 4-1: new full speed USB device using uhci_hcd and address 5
Mar 16 20:56:54 (computerhostname) kernel: [253254.136027] usb 4-1: device not accepting address 5, error -71
Mar 16 21:23:47 (computerhostname) kernel: [254867.152034] usb 1-2: reset high speed USB device using ehci_hcd and address 3
Mar 16 22:09:47 (computerhostname) kernel: [257627.152035] usb 1-2: reset high speed USB device using ehci_hcd and address 3

```


I'm not sure what the error -71 is..  anyone know?   And, the reason I chose to go with the SoftRAID is because I didn't have the money to invest in a good RAID card, and I have heard stories of the card dying, and if the card dies all data is lost. The point of RAID is redundancy and having all your eggs on one RAID card didn't sound appealing to me.  Also, I like having the ability to plug my drives into any ubuntu computer and mount the RAID, then on top of that, I didn't have a good way to power 6 sata drives easily.  I think I would have had to get an additional power supply right?

I am currently rebuilding the raid, and then when that is done (3ish hours left) I'll make sure I do the proper entries in the mdadm.conf  and then we'll see what happens.  :)

Thanks again!

---

### Post by disabledaccount on 2011-03-19
> **Vegan said:**
> Get a controller card then you woes will go away.

Software RAID is begging for trouble.Are you a bot? Or you just trolling?
It seems that You copy-paste the same sentence in many raid related topics. Your "IT" page is a proof that You don't have even basic knowledge about Raid, so please stay happy with your old good Barracuda and stop talking about things that You even haven't seen.

dsmacman: ok, so we have good trace of the problem. Unfortunatelly it seems to be hardware fault. It can be damaged USB cable, damaged USB<->SATA interface in one of Your disks, electrically overloaded USB HUB, damaged MB or physically damaged USB connector.
At first I suggest to launch log viewer, stop md device then disconnect/connect again every array member. This way You'll find: a) which disk is connected to USB 4-1, and b) what is more important - if this is damaged connector or cable, then You will generate similar errors by touching/moving the device or its USB cable.

How those disks are powered? - do they have additional power supply or additional USB cable or just single cable?

---

### Post by rubylaser on 2011-03-19
> Are you a bot? Or you just trolling?
It seems that You copy-paste the same sentence in many raid related topics. Your "IT" page is a proof that You don't have even basic knowledge about Raid, so please stay happy with your old good Barracuda and stop talking about things that You even haven't seen.

This made me laugh.  This is spot on my answer.  How is a Hardware RAID controller the solution to USB drive disconnects?  

You do have hardware disconnects and that's one of your problems.  You'll need to have a proper mdadm.conf file if you want to use mdadm, so please run the commands that I posted.  Then the USB problem, looks like tomazzi's ideas are a good place to start.

>  Ididn't have a good way to power 6 sata drives easily. I think I would have had to get an additional power supply right
Powering 6 SATA drives is easy to do if your PSU has one rail. Something like this would have no problem running your machine and 6 disks.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16817139017]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817139017")

---

### Post by Vegan on 2011-03-19
A good RAID card is a lot less headache.

---

### Post by dsmacman on 2011-03-20
Okay, so the rebuild completed and the raid is running.   I followed your commands and now my mdadm.conf is this:

```
DEVICE /dev/sd[befgij]
HOMEHOST (computerhostname)
MAILADDR root@localhost
ARRAY /dev/md0 level=raid5 num-devices=6 metadata=00.90 UUID=e155c385:ec96168d:a0999c3a:db015e5b
```

That look right?   Question though.. doesn't the assignment of /dev/*** change per reboot?  So why would I specify which addresses it is if they change?

I will play with the cords and dismounting of the drives tomorrow when I am physically next to the computer, but just some preliminary information:  This is the second computer I am trying this on (the first had the same problems, so I upgraded to a more powerful machine), so I would like to say that it is either something with the drivers, the USB cords, or the drives themselves.. would that be a reasonable assumption?

Thank you for that link to the PSU, if this doesn't work out for me, I might follow that option.  =)

Thanks again for your help!

---

### Post by rubylaser on 2011-03-20
This looks like a valid mdadm.conf.  Two things I'd change.  First change your metadata portion of the ARRAY line to look like this...
```
metadata=0.90
```
Basically removing the first zero.  This is prevent from showing this error. **mdadm: metadata format 00.90 unknown, ignored.**

Second, your array question is a good one.  These are the acceptable values for the DEVICES section in your situation without partitions: It's either a comma separated list of device names (/dev/sdb,/dev/sdc,etc) or partitions. 
```
DEVICE /dev/sda,/dev/sdb,etc
```
Or with a wildcard...

```
DEVICE /dev/sd*
```
Alternatively, a DEVICE line can contain the word partitions. This will cause mdadm to read /proc/partitions and include all devices and partitions found there. So, in your case, partitions is still acceptable. I would use **partitions** in the DEVICE line, that way device postions don't matter at all.

---

### Post by dsmacman on 2011-03-21
Quick Update:

Everything is still working, my raid has been fine and I've transferred about 750GB of data to it trying to stress test it and it has handled it without issue.  (though takes a little while to copy :) )

I haven't even see any USB disconnects in the kern.log file.   So, I plan on keeping this thread open just a bit longer waiting to see what happens.. hopefully that's okay. :)


EDIT:

Well it is still working as of March 28th.. so I'm going to close this thread out and hope I don't have any more issues!   Thanks for your help.  For anyone looking at this: the only thing that I changed was adding the raid configuration into mdadm.conf  perhaps that was all I needed to do to fix my problems.

---

