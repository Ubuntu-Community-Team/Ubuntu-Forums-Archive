---
title: "logical names giving me the run-around (LITERALLY!)"
date: 2011-03-16
forum: Server Platforms
---

### Post by TechSupportx86 on 2011-03-16
Ok so today i decided to re-work my home server. Added a new 1TB SATA HDD, replaced the 6GB boot drive with an 80GB SATA, put my 120GB and my 160 GB IDE Drives back in and installed fresh. 

[COLOR=Red]Now the problem[COLOR=Black] i am having[/COLOR][/COLOR] is pretty odd and i can't seem to fix it. Everytime i boot up it sees all 4 hard drives and assigns a logical name to each (/dev/sda or sdb like it normally does) however after i setup fstab to mount each drive to a path (/media/drive) and reboot, it **_CHANGES_** the logical name to one that is un-used (like sdg or sdh), so i go back in to fstab and change the logical name, reboot, does it again but it goes back to what it was before i changed it (sda and sdb).

As you can see the title really does say it all. I have re-installed 3 times with all drives removed and adding one by one but to no avail. Now i'm *thinking* it's because i'm using 2 SATA drives? I have never had this problem before, then again my boot drive was always IDE.

Anyone got any ideas???

---

### Post by arubislander on 2011-03-16
> **TechSupportx86 said:**
> Anyone got any ideas???

You could try using the UUID instead of the logical names in fstab. They should stay put... There are several ways to find the right UUID for your drive, but the one I always use is 
```
~$ ls -al /dev/disk/by-uuid
```
On my test VM the output is
```
total 0
drwxr-xr-x 2 root root 100 2011-03-16 10:03 .
drwxr-xr-x 6 root root 120 2011-03-16 10:03 ..
lrwxrwxrwx 1 root root  10 2011-03-16 10:03 1905a0c5-4dce-4762-9d8b-57691d5285ee -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-03-16 10:03 1e4bfb47-af7a-4f6f-9d5a-d7169f923678 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-03-16 10:03 c59b351f-b057-43c2-8d23-28edacc74ccc -> ../../sda1

```

---

### Post by BkkBonanza on 2011-03-16
Definitely use the UUID method. There is just no guarantee which order the drives will get detected and that often determines how they get labelled. 

Once you know the UUID as shown above just edit your fstab and put in 

UUID=blahblahlongcodehere /mountpoint 

instead of using 

/dev/sda  /mountpoint

Simple change.

This is the way Ubuntu always installs by defult now so you must be manually trying to force it to use device names but that method is not reliable now.

eg.
my fstab has,

# /dev/sda2
UUID=f651eaca-f066-4767-ac88-057c2aa2f381 /media	ext3	defaults	0 0

---

### Post by TechSupportx86 on 2011-03-16
UUID worked perfectly (i guess that's why the boot drive is setup that way ;))

I am assuming the problem was being caused by the new SATA drives since before that i was using IDE and never had this sort of problem. i guess the drives logical name gets assigned by what order they are detected each boot (IDE1 M/S then IDE2 M/S, or sda/sdb and sdc/sdd) with SATA getting detected first only 50% of the time, and one of the IDE drives the other, mixing up the logical names each boot.

I've read a few pages on UUIDs and using the UUID seems to be the best way to mount. i mean if GRUB uses it and ubuntu sets it up using the UUID, it can't be the wrong way ;)

Thank you **arubislander **and **BkkBonanaza**, solved my problem and it didn't take 3 days :D

---

