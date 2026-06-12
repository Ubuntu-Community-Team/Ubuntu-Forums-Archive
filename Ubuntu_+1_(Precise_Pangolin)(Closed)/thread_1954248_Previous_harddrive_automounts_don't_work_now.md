---
title: "Previous harddrive automounts don't work now"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Sith Lord Kyle on 2012-04-07
After I updated to 12.04, all the previous harddrives I had automounting stopped working.  I can just enter "sudo mount /dev/sdb1" in Terminal to mount it to the directory set up in fstab... but why aren't they mounting at boot?  What changed in 12.04?

---

### Post by ajgreeny on 2012-04-07
> **Sith Lord Kyle said:**
> After I updated to 12.04, all the previous harddrives I had automounting stopped working.  I can just enter "sudo mount /dev/sdb1" in Terminal to mount it to the directory set up in fstab... but why aren't they mounting at boot?  What changed in 12.04?
Proably the /etc/fstab file changed, or if the old version contained /dev/sdx# naming, instead of UUID,perhaps the system has re-detected the disks with different partition numbers.

Or perhaps the old mountpoint folders have disappeared from the filesystem on doing the distro upgrade.

---

### Post by Sith Lord Kyle on 2012-04-07
The fstab file was indeed updated, but it does now contain the UUID instead of /dev/sd** naming.

The original mountpoint folders are still there, when I run the "sudo mount /dev/sd**" command on those harddrives they mount to those folders.

This is rather odd they automount... but I have no idea why other than perhaps a glitch in 12.04.

HOWEVER... it should be noted that these are all NTFS drives.  Think that makes a difference?

---

### Post by ajgreeny on 2012-04-08
Let's see the fstab file; that will tell us plenty about the situation.

---

### Post by macstevejb on 2012-04-08
Automount following instructions in this link, in the udisks section:

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

regards :p

---

### Post by Sith Lord Kyle on 2012-04-09
The fstab file being used...

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=2d0ed33b-4a12-4488-8da7-4cd761221b81 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=4c3c5c7e-a7b1-459c-9867-bdc9840f2436 none            swap    sw              0       0
# Studio - library partition at /dev/sdb2
UUID=59fef921-df7c-4127-bc26-87c4ccd9439c	/Studio	ext4	defaults	0	2
# Radio - music partition at /dev/sdd1
UUID=5FC0B65B565D4AD5	/Radio	ntfs	defaults	0	3
# Channel - video partition at /dev/sdc1
UUID=495A2DC91285F3C6	/Channel	ntfs	defaults	0	4
# Shank - Windows partition /dev/dda1
UUID=1D84B25F0903A409	/Shank	ntfs	defaults	0	5
# Windows Games - library partition at /dev/sdb1
UUID=01E3FA0672DD8107	/Locker	ntfs	defaults	0	6


And I'll check out that link and see if any of that helps.

UPDATE:
Yeah, that link was pretty much useless, but thanks for the attempt, sir. Just trying to figure out why the updated fstab in 12.04 doesn't work.

---

### Post by ajgreeny on 2012-04-09
OK, now let's see the output of ```
sudo blkid -cu
``` which will show the UUIDs of all partitions on the machine.  We can then compare that with your fstab.

---

### Post by Morbius1 on 2012-04-09
Hope you don't mind the interruption but the 3, 4, 5, 6 at the end of your ntfs partitions are not correct. It can only be 0, 1, and 2. And in the case of NTFS it's best to have it set at 0. I don't think it will do any harm to leave them as it is since I think (?) the system will just ignore it but it looks funny.

The last digit determines the relative order of a files system check at boot time. The root partition usually is set at 1. Other linux partitions are set at 2 ( do after root ) and in the case of ntfs it's set at 0 ( never ).

---

### Post by ajgreeny on 2012-04-09
> **Morbius1 said:**
> Hope you don't mind the interruption but the 3, 4, 5, 6 at the end of your ntfs partitions are not correct. It can only be 0, 1, and 2. And in the case of NTFS it's best to have it set at 0. I don't think it will do any harm to leave them as it is since I think (?) the system will just ignore it but it looks funny.

The last digit determines the relative order of a files system check at boot time. The root partition usually is set at 1. Other linux partitions are set at 2 ( do after root ) and in the case of ntfs it's set at 0 ( never ).
You're right, of course. I did not notice those figures!  Will still be useful to check the blkid output with the fstab file

---

### Post by Sith Lord Kyle on 2012-04-09
BLKID spit out the following...

/dev/sda1: LABEL="Studio" UUID="59fef921-df7c-4127-bc26-87c4ccd9439c" TYPE="ext4" 
/dev/sdb1: LABEL="Shank" UUID="1D84B25F0903A409" TYPE="ntfs" 
/dev/sdb2: UUID="2d0ed33b-4a12-4488-8da7-4cd761221b81" TYPE="ext4" 
/dev/sdc1: LABEL="Radio" UUID="5FC0B65B565D4AD5" TYPE="ntfs" 
/dev/sdd1: LABEL="Channel" UUID="495A2DC91285F3C6" TYPE="ntfs" 
/dev/sde1: LABEL="Games" UUID="01E3FA0672DD8107" TYPE="ntfs" 

I just changed the last digit in fstab to zero on all those lines.  Oddly, they worked fine that way in 10.04... before I updated to 12.04.

---

### Post by Sith Lord Kyle on 2012-04-09
Okay, so changing the last digit in each NTFS line to zero worked!  Not sure why it was accepted in 10.04, but it clearly was not okay in 12.04.

Thanks for the assistance!  Now on to a litany of other problems with Precise.

---

### Post by Morbius1 on 2012-04-10
Actually , I never expected my recommendation to fix anything. I only suggested it because it was syntactically incorrect. My assumption that anything greater than 2 would be ignored must not be true.

---

