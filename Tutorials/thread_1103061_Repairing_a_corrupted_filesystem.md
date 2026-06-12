---
title: "Repairing a corrupted filesystem"
date: 2009-03-22
forum: Tutorials
---

### Post by WitchCraft on 2009-03-22
You can repair a corrupted filesystem with the program "fsck".



AN IMPORTANT THING FIRST:

File systems must be unmounted, you cannot repair them while they are running. 
So fsck must ALWAYS be run on an UNmounted filesystem.
**Running fsck on a mounted filesystem can do SEVERE damage.**

[B][COLOR="Red"]Be sure to specify the file system type using the -t option. 
Note: NOT using -t ext3 on a ext3 system WILL result in MORE corruption! 
Fsck by default assumes an ext2 file system.[/COLOR][/B]



A quick fsck options overview:

Many options for **fsck** exist, but the most important are: 
  **-f**    which performs a FAST check
 **-p**    which fixes minor problems without user interaction
 **-y**    which gives permission to correct every problem found 
 **-n**    which indicates to only search (and not correct) problems 
 
 

 See the man page for **fsck** for more detailed information. 








The most simple variant to run fsck is to force fsck on restart, and then restart your system:
```


sudo touch /forcefsck


```











The other option is to swich the system to runlevel 1 (logs-out any userRunning fsck on a mounted filesystem can do SEVERE damage), unmount all partitions. run fsck & repair, remount all drives, increase the runlevel to 3 and continue.





1) Take system down to runlevel one (make sure you run all command as root user):
**# init 1**

 2)Unmount file system, for example if it is /home (/dev/sda3) file system then type command:
**# umount /home**

OR

**# umount /dev/sda3**

 3) Now run fsck on the partition:

**# fsck /dev/sda3**
 However be sure to specify the file system type using -t option. Recenly one of our sys admin run the command on ext3 file system w/o specifying file system. Result was more corruption as fsck by default assumes ext2 file system.
**# fsck -t ext3 /dev/sda3 **
OR
**# fsck.ext3  /dev/sda3 **
 Tip if you don't know your file system type then typing mount command will display file system type.
 fsck will check the file system and ask which problems should be fixed or corrected. If you don't wanna type y every time then you can use pass -y option to fsck.
**# fsck -y /dev/sda3**
 Please not if any files are recovered then they are placed in /home/lost+found directory by fsck command.


 4) Once fsck finished, remount the file system:
**# mount /home**

 5) Go to multiuser mode
**# init 3**
 Read man page of fsck for more information. Make sure you replace /dev/sda3 with your actual device name.

---

### Post by Th3Professor on 2009-04-22
Okay, I'm worried about something here... my system started behaving odd, locked up while running, had to force a reboot, then had to get the bios to boot into the system, well then it put me into the "maintenance" mode (had to log into root). I did what it said, fsck, and "i.e. no -a or -p", so I just did a plain fsck on the / but (which is /dev/sda5 in this case), only I didn't catch the ext2 default, and mine is ext3. I went ahead and ran it:

fsck /dev/sda5

And I selected "yes" to everything.

Now I suspect it's even worse, since it was expecting ext2 with the command I used.

Can I fix it?

I want my *nix back. I had to resort to Windows (right now), only I'm hoping this is only temporary.

My /home is in the / partition. It is very important that I recover that data, as well as actually getting the system running again.

Please help. Thank you!

---

### Post by WitchCraft on 2009-04-30
> **Th3Professor said:**
> Okay, I'm worried about something here... my system started behaving odd, locked up while running, had to force a reboot, then had to get the bios to boot into the system, well then it put me into the "maintenance" mode (had to log into root). I did what it said, fsck, and "i.e. no -a or -p", so I just did a plain fsck on the / but (which is /dev/sda5 in this case), only I didn't catch the ext2 default, and mine is ext3. I went ahead and ran it:

fsck /dev/sda5

And I selected "yes" to everything.

Now I suspect it's even worse, since it was expecting ext2 with the command I used.

Can I fix it?

I want my *nix back. I had to resort to Windows (right now), only I'm hoping this is only temporary.

My /home is in the / partition. It is very important that I recover that data, as well as actually getting the system running again.

Please help. Thank you!

umount /path/to/device
fsck -t ext3 /dev/whatever

Good luck (you need it)!

---

### Post by Th3Professor on 2009-04-30
oh i forgot about this thread... i fixed it. thankfully! fortunately it was nothing major. though lately the computer has been locking up on me about 5 seconds after the graphics start freaking out. this hasn't happened so much lately but for a while it was happening every day about 1x or 2x per day. everything's up to date too (graphics drivers, kernel, system stuff, etc)

---

### Post by Ashishdk on 2013-03-18
Just upgrade the Ubuntu os then you see ur data is 100% save

---

### Post by varunendra on 2013-03-18
Thread too old to be bumped. Closed!

---

