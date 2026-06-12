---
title: "Wiping HD during 8.04 Partitioning"
date: 2009-01-10
forum: Server Platforms
---

### Post by dpeters on 2009-01-10
A corrupted OS is on the HD and I am trying to do a re-install.
When you get to the partitioning step the preexisting data on the disk messes up the partitioning program even if you delete the partitions and write changes to the disk. I need to wipe it clean so this works. Is there a way to do this from the install CD.

---

### Post by whoop on 2009-01-10
Boot from the livecd (select try ubuntu) when it's booted run 
```

sudo gparted

```

whipe all partitions from your harddrive (this will ERASE everything). Apply the changes.

Do an (optional) restart, and install ubuntu

---

### Post by tubezninja on 2009-01-11
If all else fails, try running [dban]("http://www.dban.org/") on it and then partitioning.

---

### Post by onering on 2009-01-11
This progeam wipes all sectors on the disk inlcluding all partitions and the boot sector. It costs $40.

[http://www.whitecanyon.com/wipedrive-erase-hard-drive.php](http://www.whitecanyon.com/wipedrive-erase-hard-drive.php)

---

### Post by dpeters on 2009-01-19
I just finished using gparted to delete all partitions from both drives, then created one new partition and formatted it Fat32.
Surely changing the FS to a different one 
Back to the install 8.04 install CD, created all the partitions on both drives. Then I setup the RAID devices. The very next window should show 5 partitions on each of the drives. 
Problem: it only shows sda1, sda8 and sdb1, sdb8. 
So much for gparted getting rid of all the data from a previously RAID array.
I also tried "dban" and it croaked somewhere between the first and second pass in the wee hours. By the way all this works correctly on new disks from the store the first time.

---

### Post by redroad55 on 2009-01-19
It may be trying to remember a previous change for example if you are trying to set up partitions and you make a mistake and hit back until you actually reboot the install cd it has no alternative but to go to the next letter or number .. I hope I was clear enough .. best to you

---

### Post by redroad55 on 2009-01-19
I use  a tool from acronis that has a DOD wiping tool that makes 4 pases .. I know both western digital and seagate provide a dos tool depending on your hard drive free of charge just go to there web page and download

---

### Post by dpeters on 2009-01-19
I had removed the drives from the server and attached them to a Linux desktop. I ran gparted (about as self explanatory as you can get) from there and saved everything, returned the drives to the server and booted the install CD. 
I also noticed the partitions created from the install CD are not in sequence (1,2,3,4,5) nor are they in the order in which I created them. I also noticed that both gparted and the install CD do not do a full format of each partition. It only took seconds to format the partitions. So data is still out there on the disk. Didn't I see a simple way to use the dd comand to write zeros to either a file, partition or a drive?

---

### Post by redroad55 on 2009-01-19
I could be wrong on this but the mbr (master boot record is replaced at new install hence the temporary number issue)..Without a full wipe (2 or more passes) the original assignment of the mbr is still in place and holding the identity of the previous config. so gparted has to go one higher on everything ..I hope this explains it ..By the way witch brand hard drives are you running ?

---

### Post by redroad55 on 2009-01-19
Is there a cd rom or floppy drive in the server ?

---

### Post by dpeters on 2009-01-23
Problem solved.
Drives are Seagate barracudas.
I found a discussion elsewhere about a challenge and reward for attempting to recover a couple files from an HD after the linux command dd was used to write all zeroes to all sectors. Several professional data recovery companies declined admitting there was nothing on the drive to recover. This was exactly what I was looking for. So I did a dd if=/dev/zero of=/dev/sda bs=10MB conv=noerror,sync. Then I went to bed. The next morning it said 750GB written and no errors. Repeated it on the b drive. Booted the 8.04LTS install CD, set up the partitions, RAID arrays and file systems and finished the install without a hitch. This was done from the 8.10 Desktop CD booted standalone. 
Previously I had tried dban (couldn't get it to run), gparted, and dd zeroing the 1st 100 blocks and setting up a completely different file system and formatting it. Install always failed.

---

