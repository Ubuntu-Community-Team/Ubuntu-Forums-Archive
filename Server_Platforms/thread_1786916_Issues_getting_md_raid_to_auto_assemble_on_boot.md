---
title: "Issues getting md raid to auto assemble on boot"
date: 2011-06-20
forum: Server Platforms
---

### Post by sescandor on 2011-06-20
I have Ubuntu 10.10 (maverick) and I'm using mdadm 3.1.4. 

I have created a RAID 10 using imsm as the metadata, and this runs successfully if I assemble the RAID from the command line. My question is: How do I get the RAID to auto assemble when I boot the system? I would like to be able to mount the RAID when the system starts up (but the OS is on a separate disk altogether). What I've found out so far is that I must do a ```
update-initramfs -k all -u
``` AFTER I've modified the /etc/mdadm/mdadm.conf file. This is what I've got in my configuration file:

```

HOMEHOST Volume0
ARRAY metadata=imsm UUID=46e68921:eea24d1d:e933eee8:192d55bc
ARRAY /dev/md/Volume0 container=46e68921:eea24d1d:e933eee8:192d55bc member=0 UUID=b39c8d9d:ab2fcd08:f4559292:981754f1

```

(I know that the RAID assembles just fine (on command-line) using "sudo mdadm -As".)

BUT what happens is that when I reboot my server, and then do "ls -l /dev/md*" there is no listing at all for any RAID devices. I actually have to run the assemble command on command line and that is when I see listings for RAID devices under /dev. What am I missing?

---

### Post by ian dobson on 2011-06-20
Hi,

Here's my mdadm.conf

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR i.dobson@planet-ian.com

# definitions of existing MD arrays

# This file was auto-generated on Sat, 19 May 2007 17:11:35 +0200
# by mkconf $Id: mkconf 261 2006-11-09 13:32:35Z madduck $

DEVICE  partitions

ARRAY /dev/md0 level=raid1 num-devices=4 metadata=0.90 UUID=4c164070:fb03e2c5:f1249533:23a13f7b
   devices=/dev/sda1,/dev/sdb1,/dev/sdc1,/dev/sdd1
ARRAY /dev/md1 level=raid5 num-devices=4 metadata=0.90 UUID=bae99b90:153e32ae:f1249533:23a13f7b
   devices=/dev/sda2,/dev/sdb2,/dev/sdc2,/dev/sdd2
ARRAY /dev/md2 level=raid0   num-devices=3 UUID=73a20df2:2fd838f5:f1249533:23a13f7b
   devices=/dev/sde1,/dev/sdf1,/dev/sdg1

```

Mine has several options more and I use the local host name for the owner of the array. I'm also not sure about using HOMEHOST Volume0 and /dev/md/Volume0, that looks strange to me.

Regards
Ian Dobson

---

### Post by sescandor on 2011-06-20
Thanks Ian - I will change the HOMEHOST to match yours and see what I get with that. Did you have to do ```
update-initramfs -k all -u
``` when you changed your mdadm.conf?

---

### Post by ian dobson on 2011-06-20
Hi,

I always run update-initramfs if I change anything that could effect the boot process.

Thinking about it, if the CREATE line in mdadm is missing mdadm won't auto assemble the array if auto=yes is missing

Regards
Ian Dobson

---

### Post by sescandor on 2011-06-24
So I've been able to find a solution to this issue. I hope the following will help someone if they run into the same thing:

Issue:

 * Using Ubuntu 10.10 and mdadm 3.1.4 - Since mdadm 3.1.4 is not in Ubuntu 10.10 repository, built mdadm 3.1.4 from source and installed.
 * When rebooting system, RAID is not assembled automatically, and the "mdadm -As" was needed to be run on the command line in order to start the RAID.

Solution:

 * Create a shell script (let's call it mdraid.sh) and place into /etc/init.d. Change the file permissions of mdraid.sh so that it is executable (using chmod + x). Within mdraid.sh you'll need so call mdadm -As, and the script looks something like the one found in: [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

 * Run "sudo update-rc.d mdraid.sh defaults"

That was what I needed to do to get this to auto assemble :)

---

### Post by ian dobson on 2011-06-24
Hi,

OK that's interesting. I've never had to do that. I always though that installing mdadm added hooks to update-initramfs, so that mdadm is included in the image and the required scripts where called automagically on boot.

What mdadm scripts do you see in /usr/share/initramfs-tools/scripts/init-premount ?

Regards
Ian Dobson

---

### Post by sescandor on 2011-06-24
Hi Ian,

When I took a look at the contents of /usr/share/initramfs-tools/scripts/init-premount/ I actually only see two scripts (which don't appear to be mdadm related): brltty and lvm2. I think the reason why I had to add my own init script was because I built from source, and I had to "ubuntu-ize" it myself? (just a guess).

---

### Post by ian dobson on 2011-06-24
Hi,

That would explain everything. If you install ubuntu normally and add mdadm through apt-get then the scripts are automagically added.

Regards
Ian Dobson

---

### Post by mszmansky on 2011-06-24
I had a perfectly functioning RAID 1 array setup and working on ubuntu server 11.04.  I rebooted the machine and it stopped working.  It now says that I cannot assemble the array.  The error when I try to assemble it is device /dev/sdb1 has no superblock - assembly aborted.  What is going on?  I have had countless number of issues trying to get RAID setup on this machine.  Not sure how to make it work.  Can someone help?  Thanks.

---

### Post by ian dobson on 2011-06-25
> **mszmansky said:**
> I had a perfectly functioning RAID 1 array setup and working on ubuntu server 11.04.  I rebooted the machine and it stopped working.  It now says that I cannot assemble the array.  The error when I try to assemble it is device /dev/sdb1 has no superblock - assembly aborted.  What is going on?  I have had countless number of issues trying to get RAID setup on this machine.  Not sure how to make it work.  Can someone help?  Thanks.

Hi,

I think it would be better to open a new thread rather than posting here.

Regards
Ian Dobson

---

