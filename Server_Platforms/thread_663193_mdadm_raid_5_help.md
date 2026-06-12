---
title: "mdadm raid 5 help"
date: 2008-01-09
forum: Server Platforms
---

### Post by modulok on 2008-01-09
I used the following link to setup a 5 disk [320gb maxtor sata hdds] for my home server (ubuntu gutsy)

[http://www.evileyez.org/quick-and-dirty-linux-software-raid5/](http://www.evileyez.org/quick-and-dirty-linux-software-raid5/)

I have an ICY DOCK 5 hard drive hot swappable enclosure with the drives installed. I noticed the other day (while copying a few GBs of data, that one of the drive lights wasn't blinking.

I restarted, and the same thing would happen. I did a mdadm --detail /dev/md0 to notice that the 2nd drive was "removed". I did this next:

# Managing the RAID device.
    * Setting a disk faulty/failed:
      # mdadm –fail /dev/md0 /dev/hdc1
    * Removing a faulty disk from an array:
      # mdadm –remove /dev/md0 /dev/hdc1
    * Clearing any previous raid info on a disk:
      # mdadm –zero-superblock /dev/hdc1
    * Adding a disk to an array:
      # mdadm –add /dev/md0 /dev/hdc1

It never finishes and the drive goes into "faulty spare" mode. I have formatted the bad drive and tried to readd it, but nothing has rebuilt 100%. In the system log it gives an error about a bad block, but at different numbers each time.

Running a quick HDD Fitness Test (Hitachi CD) said the drive is healthy. Also the ICY DOCK drive light is green, meaning its healthy. To me there is an issue in Linux that I am unsure of. Right now I am running the drive in Windows, doing a disk check for bad sectors. (its about 75% done as of this post)

Has anyone had this happen? Or any ideas for me? As of right now I can still get to all of the data, I might considering copying it elsewhere for the time being, until I get this drive working and get my redundancy back.

I am open to any help that anyone has, thanks in advance.

---

### Post by modulok on 2008-01-11
nobody on this?

do I really have to just recreate the array and format it?

---

### Post by fozy on 2008-01-11
My first guess would be you're replacing hdc1 when you said the second drive is failing, which I would guess is hdb1.  Maybe provide some more info on your drive setup.

---

### Post by modulok on 2008-01-11
the hdc1 was just a reference in the copy/paste I did from the site listed above.

in reality, the failed drive is sdd1, but that doesn't matter. I just need to know how to get the drive working in the array so I can have my redundancy back with the raid 5 setup.

The drive is good, it works fine in windows, no bad sectors in windows check disk.

---

### Post by phyerlight on 2008-01-20
I've had something similar happen to me in a raid 0 setup that I have. I believe that it was a power issue.

Either the power supply was starting to fail or I was getting an inconsistent level and the power supply wasn't leveling it out properly. A new (better) supply fixed things.

---

