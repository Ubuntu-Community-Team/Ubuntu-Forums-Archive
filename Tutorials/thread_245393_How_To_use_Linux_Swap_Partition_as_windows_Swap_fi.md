---
title: "How To use Linux Swap Partition as windows Swap file"
date: 2006-08-27
forum: Tutorials
---

### Post by jsnipe on 2006-08-27
I came across this neat little trick while researching another issue, installed it and have been running it for about two weeks.  That being said, I only use win XP for morrowind, so I can't say I've fully verified this programs functionality.

How to use linux swap partition as windows swap file:

1.     Go to the website below, and download the swapfs zip file to a windows accessible folder:
[http://www.acc.umu.se/~bosse/](http://www.acc.umu.se/~bosse/)


2.     Write down the location of your linux swap partition (for example, mine is the 4th partition on the first drive; /dev/hda4 or (hd0,4).  hda=hd0, hdb=hd2, etc...  If your drive is sda[COLOR="DarkOrange"]X[/COLOR], check your bios settings to determine which drive it is.
(Do not include extended partitions, only primary and logical).

3.     Extract the contents of the zip file to its own folder, and open up the file "swapfs.reg" for editing, changing the two lines that read "\\Device\\Harddisk[COLOR="DarkOrange"]0[/COLOR]\\Partition[COLOR="darkorange"]1[/COLOR]" to the location of your linux swap partition (in my case "\\Device\\Harddisk[COLOR="darkorange"]0[/COLOR]\\Partition[COLOR="darkorange"]4[/COLOR]").

4.     Copy the driver (swapfs.sys) to "%systemroot%\system32\drivers\".

5.     Reboot, and verify you swap settings under system settings, in the control panel (you may have to turn off the old paging file manually).

6.     Enjoy the extra disk space!



these instructions are also included with the zip file, along with the source code for the original program.  This works great because the swap data contained in linux and windows is forgotten after every reboot, so why not utilize the same space?

P.S- I didn't write this program, I found it while googling another issue.

---

### Post by HAARP on 2006-08-27
I'd definately use this if I still used Windoze :)
How about moving it to Howtos? Any mod?

---

### Post by jsnipe on 2006-08-27
I thought about moving it to HowTo's, but it seemed more relevant to the people still using windows (who are for the majority, gamers).  If enough people request it I suppose I could move it.

---

### Post by Laibcoms on 2007-12-22
Move it out from the gaming forums ;)

Even non-gamers will need that info.  There are people who really have no choice but to keep WinXP or WinVista installed - too many factors that prevents us from removing WinXP/WinVista even though we do not use it ourselves.  Too many reasons not to.

:)  I'm just lucky I just know the proper keywords to search and the bots still indexes this thread, so I found this thread :p

Thanks for sharing it.. useful. :D  More free space to use now!

---

### Post by goldmund99 on 2008-09-07
Thank you for the howto! But I had some problems to determine the partition number. Finally I got it using this method:

1) On Windows XP select Start->run->"cmd"

2) run "diskpart"

DISKPART> *list disk*


.     Disk n.   State       Size     Free
.     --------  ----------  -------  ----  ...
.     **Disk [COLOR="Red"]0[/COLOR]**    Ready       233 GB    0 B

DISKPART> *select disk [COLOR="Red"]0[/COLOR]*

DISKPART> *list partition*

.     Partition  n.  Type              Size     Offset
.     -------------  ----------------  -------  -------
.     Partition  1    Primary            49 GB    32 KB
.     Partition  2    Unknown           178 GB    49 GB
.     **Partition  [COLOR="Red"]3[/COLOR]**    Extended         5938 MB   227 GB
.     Partition  4    Logic            5938 MB   227 GB

DISKPART> *exit*

3) Then harddisk number is [COLOR="Red"]0[/COLOR] and the swap partition is the extended one ([COLOR="Red"]3[/COLOR])

---

### Post by Bastaard on 2008-09-09
This should definitely be in the How To section. I for one am not a gamer and still use this trick.

---

### Post by Perfect Storm on 2008-09-09
Going to move it then.

---

### Post by Steve Fisher on 2008-09-10
This seems like a great idea, but before I go and do something terrible, could someone just look over this for me please?

I've got a single hdd. There's Dell utilty partition (FAT) at the start of the drive, then XP in the second, primary partition. Next is my Ubuntu patition (ext3), then an extended partition which contains my Home partition and my Swap partition.

So am I right in saying that I need to edit the reg file to say disk 0, partition 4 (the extended container)? Even though Ubuntu sees the swap as partition 6?

. Disk n. State Size Free
. -------- ---------- ------- ---- ...
. Disk 0 Online 28 GB 0 B

DISKPART> select disk 0

DISKPART> list partition

. Partition n. Type Size Offset
. ------------- ---------------- ------- -------
. Partition 1 OEM 47 MB 32KB
. Partition 2 Primary 5114MB 47MB
. Partition 3 Unknown 9GB 5162MB
. Partition 4 Extended 14 GB 14GB
. Partition 5 Logical 13 GB 14GB
. Partition 6 Logical 957 MB 27 GB

---

### Post by CapnBoost on 2009-12-07
THREADZURRECTION!

I used this, rebooted in to windows (haven't booted back in to Ubuntu Karmic yet) and now I have c:/ (20gb) and s:/ (20gb)

Now i realize that the reg file makes s:/, but why does it trick windows in to thinking that s:/ is a clone of c:/?  Is there any way that I can make s:/ accurately display the swap space?  There's no change in DISKPART, there's no change in the size of my windows partition displayed in my computer or otherwise.

What gives?

Edit: signed in and editing from karmic, no change at all on this side.

---

### Post by 13eastie on 2010-06-30
Had just been thinking about this idea and was pleased to find a thread with a potential solution.

Can anyone confirm that the advice here is still valid for Windows 7 / Lucid?

---

### Post by faheyd on 2010-11-17
> **13eastie said:**
> Had just been thinking about this idea and was pleased to find a thread with a potential solution.

Can anyone confirm that the advice here is still valid for Windows 7 / Lucid?
OK, this works on windows 7 64bit.  However, the swapfs.sys file is an unsigned driver. That means it doesn't normally get loaded. After reading the install/readme files and editing the reg file, you 'click' on the reg file to install the settings. Copy the sys file to your C:\windows\system32\drivers directory.
Please have AVG or another anti virus running on your win7 box.
I used [http://www.ngohq.com/home.php?page=dseo](http://www.ngohq.com/home.php?page=dseo) to put win7 in test mode. This allows the boot process to load the unsigned driver.
However, my AVG immediately wanted to quarantine the DSEO app and its associated files. I let AVG do that. I rebooted and now I have an S: drive that I can use for windows 7 swap area.
In the lower right hand side of the screen I now see a graphic overlay saying my windows 7 is in Test Mode.  
Searching the web says this is not a problem, unless I load up some 'bad' driver.
I'm going to have to say, **[SIZE="5"]this not a good thing overall[/SIZE]** for win 7 64bit users. I did try to get the dseo app to 'sign' the driver, but that didn't work, as AVG wanted to remove junk that dseo put in the windows directory. 
However, if you are willing to take a risk, OK. I've read the entire dseo web site and it seems OK, that it's a legit thing and that the AVG tools are giving 'false' alerts. Hmm, I'll leave that up to you to decide.

Hopefully the originator of the swapfs.sys file can find a way to 'sign' the driver.

---

### Post by imwithid on 2011-02-01
> **faheyd said:**
> OK, this works on windows 7 64bit.  However, the swapfs.sys file is an unsigned driver. That means it doesn't normally get loaded. After reading the install/readme files and editing the reg file, you 'click' on the reg file to install the settings. Copy the sys file to your C:\windows\system32\drivers directory.
Please have AVG or another anti virus running on your win7 box.
I used [http://www.ngohq.com/home.php?page=dseo](http://www.ngohq.com/home.php?page=dseo) to put win7 in test mode. This allows the boot process to load the unsigned driver.
However, my AVG immediately wanted to quarantine the DSEO app and its associated files. I let AVG do that. I rebooted and now I have an S: drive that I can use for windows 7 swap area.
In the lower right hand side of the screen I now see a graphic overlay saying my windows 7 is in Test Mode.  
Searching the web says this is not a problem, unless I load up some 'bad' driver.
I'm going to have to say, **[SIZE="5"]this not a good thing overall[/SIZE]** for win 7 64bit users. I did try to get the dseo app to 'sign' the driver, but that didn't work, as AVG wanted to remove junk that dseo put in the windows directory. 
However, if you are willing to take a risk, OK. I've read the entire dseo web site and it seems OK, that it's a legit thing and that the AVG tools are giving 'false' alerts. Hmm, I'll leave that up to you to decide.

Hopefully the originator of the swapfs.sys file can find a way to 'sign' the driver.

I'm not quite familiar with all of the new features that come with Windows 7 x64 (I've helped set up only one system using Home Premium Edition), but according to the readme.txt file that comes with SwapFs-3.0.zip, there is a way to fix this, I suppose:

> Reboot. If using an unsigned driver and running on the 64-bit version of Windows press F8 and select "Disable enforce driver signing".

I use Windows XP Professional x64 Edition and find this comment vague.

---

### Post by faheyd on 2011-02-06
> **imwithid said:**
> I'm not quite familiar with all of the new features that come with Windows 7 x64 (I've helped set up only one system using Home Premium Edition), but according to the readme.txt file that comes with SwapFs-3.0.zip, there is a way to fix this, I suppose:



I use Windows XP Professional x64 Edition and find this comment vague.


Wow, I'm at a loss as to what this contributes to the thread. We're trying to NOT have to press F8 on reboot, that's the whole point.
And since you're easily confused, Windows 7 - 64 bit version. :lolflag:

---

### Post by virus2547 on 2011-08-01
I'm currently using said driver on 64bit windows 7 and haven't had any problems so far.

Anyways didn't see it mentioned, you don't need any extra apps to change the code signing option. You can change it by opening up gpedit.msc and navigating to User Configuration -> Administrative Templates -> System -> Driver Installation. You can also change the behaviour when it encounters an unsigned driver (warn is a nice option ;)).

---

### Post by Perfect Storm on 2011-08-01
nwm

---

### Post by avada on 2011-08-30
> **virus2547 said:**
> I'm currently using said driver on 64bit windows 7 and haven't had any problems so far.

Anyways didn't see it mentioned, you don't need any extra apps to change the code signing option. You can change it by opening up gpedit.msc and navigating to User Configuration -> Administrative Templates -> System -> Driver Installation. You can also change the behaviour when it encounters an unsigned driver (warn is a nice option ;)).
It wouldn't work for me... At first when I installed swapfs I got a notification that win doesn't allow unsigned drivers. After I changed those settings to enabled/warn and re-did the installation process I didn't get a warning, but it also didn't work when I restarted. What am I missing?

---

### Post by avada on 2011-08-30
Ok, So I tried again, removing the registry keys then readding them. But I still got the same notification that it doesn't work.
So it seems this setting doesn't work.

---

### Post by avada on 2011-08-31
Ugh!
I had to use a tool called[Driver Signature Enforcement Overrider]("http://www.ngohq.com/home.php?page=dseo") to enable test mode and then to sign the driver. And then I had to use [another tool]("http://deepxw.blogspot.com/2008/12/remove-watermark-v03-build-20081210.html") to remove the annoying watermark. Rather ugly hacking...

It seems to work fine now. Although the swapfile is limted to 4 GB. Is that a limitation in the swap filesystem? Can it be bypassed?

---

### Post by Lolo Uila on 2011-12-25
> **CapnBoost said:**
> THREADZURRECTION!

I used this, rebooted in to windows (haven't booted back in to Ubuntu Karmic yet) and now I have c:/ (20gb) and s:/ (20gb)

Now i realize that the reg file makes s:/, but why does it trick windows in to thinking that s:/ is a clone of c:/?  Is there any way that I can make s:/ accurately display the swap space?  There's no change in DISKPART, there's no change in the size of my windows partition displayed in my computer or otherwise.

What gives?

Edit: signed in and editing from karmic, no change at all on this side.
In my case something similar happened, but that was because Windows saw my drive order differently from Linux. Linux saw my swap as /dev/sdc3 (3rd drive, 3rd partition). But Windows (7, 32 bit) saw that SAME drive as the 2nd drive.

So according to Linux I should edit the .reg file to:

\\Device\\Harddisk[COLOR="Red"]**2**[/COLOR]\\Partition3

But according to Windows it should be:

\\Device\\Harddisk[COLOR="Red"]**1**[/COLOR]\\Partition3

Once I fixed that it all worked as expected. I'm guessing this is because I have both IDE and SATA drives. Linux orders my 2 IDE drives before my SATA drive (IDE1-IDE2-SATA). Windows puts the SATA drive in-between my IDE drives (IDE1-SATA-IDE2).

Not sure if that's your problem, but hopefully this will help someone.

Aloha, Tim

---

