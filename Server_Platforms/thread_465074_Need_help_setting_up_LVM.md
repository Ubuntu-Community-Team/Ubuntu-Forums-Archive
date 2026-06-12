---
title: "Need help setting up LVM"
date: 2007-06-05
forum: Server Platforms
---

### Post by mmathur on 2007-06-05
So, i've been trying to setup LVM for my machine and it got hosed and I had to re-install ubuntu.  I didn't lose the data I wanted to keep...I backed it up on another drive and am waiting to load it back on to the system.  So here is my situation:

- Reinstalled Fiesty Fawn
- Partitioned the drive as such: 500GB hard drive with 3 partitions
[LIST]
[*]/dev/sda1 - mount point: / (15GB)
[*]/dev/sda2 - swap space (2GB)
[*]/dev/sda3 - mount point /var/lib (470GB)
[/LIST]
- ran sudo fdisk -l /dev/sda and got this:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1912    15358108+  83  Linux
/dev/sda2            1913        2167     2048287+  82  Linux swap / Solaris
/dev/sda3            2168       60801   470977605   8e  Linux LVM

MY GOAL: make the /dev/sda3 partition (/var/lib mount point) to be LVM so I can throw in another hard drive and expand the space on /var/lib.

What do I need to do in order to make the /dev/sda3 partition an LVM...and I will need to have things spelled out for me (e.g. how to create a lv group and pv group, etc).

One thing to note, I currently have the following directories in my /var/lib directory:
alsa,gdm, update-manager, and many others...
In other posts, the instructions read to unmount the parition and format it...though i had to force the partition to unmount by killing processes and this hosed the gdm and got me here...a fresh install of Fiesty Fawn and still confused on how to setup the LVM.

I would really appreciate your help.

---

### Post by umattu on 2007-06-05
I have not done this on an already running machine so I can't advise you there, but if you are doing a fresh install I can. Also I have not done this with a feisty server but rather on a Dapper server. Im sure its not that differant between the two.

First if you are doing a fresh install, in the partition manager create your partitions. next edit the partition that you would like to use as a Logical volume. In the properties you have a choice to "use as" in there select to use as a physical volume for LVM. Now hit enter to get back to the partition editor. Above the list of partitions you will see a selection of "configure logical volume manager" once in here you will see an option to "modify Volume Groups (VG)" once in here chosse "create volume group" you will have to select the volume you would like to use. Next you will be prompted to give the volume a name, once you have name the VG hit ok and you will be presented with some more choices. Choose "Modify Logical Volumes" in here the next thing you will do is to "create logical volume" you will be prompted to give the LV a name. once that is done the changes will be written to disc and your done. 

I hope this helps!!!

---

### Post by mmathur on 2007-06-06
Unfortunately, with Feisty, the partition manager didn't provide me with those options.

I am trying to create the lv on the 3rd partition (/dev/sda3 - which has /var/lib as the mount point) and I get an error because the partition is already mounted.  I can't unmount it since some processes are running on it (gdm is one of them).

Any suggestions on how to get around this?

---

