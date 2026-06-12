---
title: "Recover Windows media from   failed win 7 /Ubuntu /Wubi  hdd."
date: 2014-01-05
forum: Windows
---

### Post by preferred_user on 2014-01-05
Would like to Recover Windows media folders and files from   failed win 7 /Ubuntu /Wubi  hdd. (host drive)
to new drive. 


I have a 750gb Seagate  hdd the windows 7x64 OS  partition is fubar none of the usual recovrey
 repair methods  work startup repair Seatools .WD lifguard
etc,etc it  has bad unreadable win OS partition sectors smart drive is tripped also. it will not load windows but 
boots into  Ubuntu/wubi  just fine 




I have  Linux Ubuntu 12.04/Wubi install on the win 7 storage partition
of the old windows drive it will boot into Ubuntu/wubi  which works fine but not windows all repairs to windows partition
have failed .


I can view the media files,folders and sub folders  on the win 7 storage partition (old drive ) with Ubunto
 in the ubuntu host file folder they look fine .
  


I replaced the hdd in the PC with a clean install of win 7x64 HP 
on a new Seagate 1 TB drive win 7 PC works fine with new drive .


Problem is I would like to transfer the media files from old drive  to the new win 7 HDD
Ubunto ofc can not mount the windows host drive partitions files or move them 
or read the windows os partition just the host drive storage files 


I tried putting the bad drive as a second HDD Ubunto boots and works 
windows does not .  I'm trying to figure out a way to move the media files to the new drive.


Ubunto sees the windows OS and storage partitions but can not move /copy the windows media files 
to new windows drive. 




I Tried glary utilities and file inspector 4, etc  they only see the windows OS partition 
97 GB of 750 gb  they can't read it  or recover or move the storage files either Ubunto can only view 
the windows storage files in the Ubuntu host file folder .


The long and short of it is I would like to move or copy the Windows media  files 
from the wubi/Ubuntu host folder (old drive ) to the new windoews drive any ideas would be helpful .
I have downloaded a live CD since one problem is the wubi install is virtual on windows drive 
that was probably a mistake rather than a real  partition . lesson learned there is the new drive will get a proper linux ubuntu partition
Ofc I'm new with Linux and not very proficiant yet. I hope I explained it correctly.


best regrds

---

### Post by Mark Phelps on 2014-01-05
When you're running Ubuntu installed using Wubi, the Windows filesystem is already mounted -- under "/host" in the filesystem.

If you can access directories and files under /host, you may be able retrieve them and copy them to your new drive.

---

### Post by Bucky Ball on 2014-01-05
*Thread moved to **Other OS/Distro Support**.*

---

### Post by preferred_user on 2014-01-05
**Re/ Mark Phelps ,**

Thanks,  I tried that it presents error message stating drive is busy and won't let me move or copy any of the host files 
or  modify / manage partitions  .There are some newly found (to me ) similar threads/ discussion  I should read.
Thanks to Bucky Balls also for moving this post  to the appropriate forum .
ofc ideas /suggestions are welcome also.

---

