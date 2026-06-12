---
title: "Moving a RAID 5 array"
date: 2007-03-10
forum: Server Platforms
---

### Post by joe_geek on 2007-03-10
Hope I've put this in the right sub-forum.  I've got a software RAID 5 array that's in an old P2 box, which is my file server.  I'd like to move it to a newer box, but I don't know if it's possible to move it without losing all the data.

I don't boot off of this RAID, there is a main drive where Ubuntu is booting off of.  It's simply used for storage.  The four drives composing this RAID 5 array are connected through a PCI SATA card.

So is it possible to just move drives to the new box and the RAID will be fine? Or will I have to back up my data and rebuild the array on the new box?

---

### Post by Mr. C. on 2007-03-10
Yes, you should be able to move the RAID card and the drives.  Keep the connections in the same order to the card when you move it just to be safe.

MrC

---

### Post by joe_geek on 2007-03-10
I'm not moving the boot drive though, will this make a difference?

---

### Post by Mr. C. on 2007-03-10
Nope. The RAID card and disks have all the information they need to fully describe the array.  They can be moved as a unit.

MrC

---

### Post by joe_geek on 2007-03-10
Awesome, thanks.  I was worried that the main drive would be required because it was software raid.

---

### Post by Mr. C. on 2007-03-10
> **joe_geek said:**
> Awesome, thanks.  I was worried that the main drive would be required because it was software raid.

Hold the phone- you did say *software* RAID!  I'm very sorry, I don't know how I overlooked that.

I'm not certain about moving that configuration.  Tread carefully.

MrC

---

### Post by gciarami on 2007-03-20
Not sure if you already resolved this issue..  wanted to let you know that I just forged ahead without finding out if it would surely work and am happy to report that it's easy as cake.

The first thing you should do is run a LiveCD and test that you can get it up and running.

For me it was as simple as booting off the CD, installing mdadm, and running the following commands (your device names and arguments may vary)

# sudo mdadm --create /dev/md0 --level=5 -n 3 /dev/sda1 /dev/sdb1 /dev/sdc1

It then told me that each of the devices appeared to be part of a raid array, should I continue.. I  crossed my fingers and replied yes.

I was then told that the device was started.

A simple mount command later and I was viewing fiiles in the raid.  (I created the directory /garage manually)

# sudo mount /dev/md0 /garage
# ls /garage


I love it!

---

### Post by Linteg on 2007-03-21
Instead of using create again, assemble would do the trick, like
```
mdadm --assemble /dev/md0 /dev/hda /dev/hdb /dev/hdc
mdadm --detail --brief /dev/md0 >> /etc/mdadm/mdadm.conf
```The first command tries to assemble the drives into an array (/dev/md0) the second command adds the array's info to mdadm.conf so it will be automatically assembled when you reboot.

---

### Post by ktulu1115 on 2007-05-11
> **Linteg said:**
> Instead of using create again, assemble would do the trick, like
```
mdadm --assemble /dev/md0 /dev/hda /dev/hdb /dev/hdc
mdadm --detail --brief /dev/md0 >> /etc/mdadm/mdadm.conf
```The first command tries to assemble the drives into an array (/dev/md0) the second command adds the array's info to mdadm.conf so it will be automatically assembled when you reboot.
I'm trying to troubleshoot a spurious drive failure on my RAID array using your instructions, and on my system I didn't even have to assemble the array!  Booted off of a Feisty LiveCD, apt-get installed mdadm (set auto-detect or whatever it was at that debian-type prompt to 'all').  After mdadm was installed, the script automatically detected and assembled them, all I had to do was manually mount them.

---

### Post by joe_geek on 2007-05-11
> **ktulu1115 said:**
> I'm trying to troubleshoot a spurious drive failure on my RAID array using your instructions, and on my system I didn't even have to assemble the array!  Booted off of a Feisty LiveCD, apt-get installed mdadm (set auto-detect or whatever it was at that debian-type prompt to 'all').  After mdadm was installed, the script automatically detected and assembled them, all I had to do was manually mount them.

I did a fresh install of Dapper LTS and I didn't need to reassemble either.  Just had to mount /dev/md0 and it was good to go.

---

