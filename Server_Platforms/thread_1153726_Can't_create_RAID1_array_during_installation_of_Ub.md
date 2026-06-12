---
title: "Can't create RAID1 array during installation of Ubuntu Server 8.10"
date: 2009-05-09
forum: Server Platforms
---

### Post by Nixie Pixel on 2009-05-09
Hello, I am trying to set up a RAID1 array on two 500GB HDDs during the installation of Ubuntu Server 8.10.  I have created a primary partition set to be the physical volume for RAID on each device.  When I try to configure MD devices it tells me that there are no partitions available for RAID.  It wants me to set one as the "Linux RAID autodetect."

Only I can't find this option anywhere.  I haven't set either partition to bootable as I was intending the array to be for a file server, and I don't want to boot to it.

So what am I doing wrong?  What do I need to do to set up RAID on these two drives?

Thanks!

---

### Post by bsmith1051 on 2009-05-11
when you created the partitions did you select a format, e.g. EXT3, immediately?  You need to leave them blank (or set as "to be RAID") because the format selection has to wait until _after_ you set us the 'md' devices.

---

### Post by Crafty Kisses on 2009-05-23
Do you know if your kernel supports auto detecting? I have RAID1 working perfectly on my Gentoo system, It's fairly simple. You might have to build the auto detect feature in your kernel in some cases depending on what kernel you're using. Does this give you any results?
```
cat /proc/mdstat
```
Remember before even touching your RAID setup you need to make sure you stop the RAID devices, remember substitute your own information. You can usually do this by running:
```
raidstop /dev/md0
```
Now the partition types of the RAID arrays need to be "0xFD" for this to actually work properly. I'm also really not sure why you want auto detection on anyway. Anyways, check these links out, they're all great tutorials.

[LEFT][LIST]
[*][http://www.tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.2](http://www.tldp.org/HOWTO/Software-RAID-HOWTO-7.html#ss7.2)
[*][https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
[*][http://www.tldp.org/HOWTO/text/Linux-Promise-RAID1-HOWTO](http://www.tldp.org/HOWTO/text/Linux-Promise-RAID1-HOWTO)
[/LIST][/LEFT]

---

### Post by samosamo on 2009-05-23
probably have to clear out old raid information.

mdadm --zero-superblock /dev/sdX

---

