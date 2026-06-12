---
title: "Accessing/Mounting EXT3 in Windows 7 Beta?"
date: 2009-01-05
forum: Windows
---

### Post by insertnewsn on 2009-01-05
Hey all,

Has anybody figured out a way to access/mount an EXT3 Filesystem within Windows 7?

All the old methods have seemed to *break* in Windows 7, as they no longer install (They don't see Windows 7 as the equivalent to XP or Vista, so it cancels the installation).

Any help you guys could give would be GREAT, since I have all my music on my ext3 partition, but am forced to use iTunes/Windows to sync to my iPod Touch (Good luck to the iPod Hash group!)

Cheers!

---

### Post by solitaire on 2009-01-05
Don't think you'll see compatible software until it's an official Beta later this month. Although depending how much different W7 is from Vista / XP it might be a few weeks..

---

### Post by insertnewsn on 2009-01-06
Yeah, I was hoping that wasn't the case. Seems funny since Microsoft claims that all software that works in Vista will work in Windows 7...Apparently this isn't true, because people create software that doesn't check for whether or not it will work, but instead checks to see that "VISTA" is the name of the OS.

---

### Post by insertnewsn on 2009-01-09
Bump

---

### Post by nlindblad on 2009-01-09
ext2-IFS works ([http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)) if you change the compability setting to "Windows Vista" by right-clicking the executable => Properties => Compability => Check "Run this program in compability mode for" and select "Windows Vista".

Cheers!

---

### Post by tjwoosta on 2009-01-11
> ext2-IFS works ([http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)) if you change the compability setting to "Windows Vista" by right-clicking the executable => Properties => Compability => Check "Run this program in compability mode for" and select "Windows Vista".

Cheers! 


it dont work for me


with ompatability mode ext2-IFS installs fine but when i reboot i still cant see the ext3 drives


EDIT:  ok i got it

i had to use compatablility mode and run it as the administrator

EDIT AGAIN: lol, nevermind i don't got it, it stops working every time after i reboot

---

### Post by nlindblad on 2009-01-11
> **tjwoosta said:**
> it dont work for me


with ompatability mode ext2-IFS installs fine but when i reboot i still cant see the ext3 drives


EDIT:  ok i got it

i had to use compatablility mode and run it as the administrator

EDIT AGAIN: lol, nevermind i don't got it, it stops working every time after i reboot

What build are you on? It works fine here.

---

### Post by tjwoosta on 2009-01-11
> What build are you on? It works fine here. 

im on the official release  ( i got it from microsoft yesterday)

build 7000


ive tried everything i can think of but no matter what i do it stops working when i reboot

it works fine immediately after i install it, but as soon as i reboot i get nothing agian, then i have to uninstall it, reboot again, then install it again and repeat the process

---

### Post by nlindblad on 2009-01-11
> **tjwoosta said:**
> im on the official release  ( i got it from microsoft yesterday)

build 7000


ive tried everything i can think of but no matter what i do it stops working when i reboot

it works fine immediately after i install it, but as soon as i reboot i get nothing agian, then i have to uninstall it, reboot again, then install it again and repeat the process

I'm on build 7000 as well. Installing that driver with compability mode set and as an administrator made it work.

---

### Post by tjwoosta on 2009-01-11
hmm..  :confused:

---

### Post by SuperShoe on 2009-01-15
Are you all using Windows 7 x64?  When I try to install using compatibility and Administrator rights, I get "Setup_x64.exe has stopped working" in the middle of the install.  Is anyone else getting this or know what's wrong?

---

### Post by fatejudger on 2009-01-15
I'm also having trouble getting Windows 7 to recognize the ext3 drives after a reboot. Has anyone found a way around this?

---

### Post by doorknob60 on 2009-01-16
After reboot, it still works, bot you have to go into the control panel to IFS drives and remount them. Kinda annoying, but it still works. Beware, after I installed ext2ifs, my home partition came up with a crapload of errors, which luckily fsck didn't have a problem fixing, but it was a major PITA. No clue if it was caused by Windows or not, but you never no. No data was lost during this though, but the automatic drive check on startup didn't do the trick I had to run it manually before it would even let me mount it.

---

### Post by eleifsp on 2009-01-20
This hasn't worked for me.  I put the install into both compatibility mode and run as administrator, and whenever I try to open my linux drive (drive X in this case), it asks me to format it.  

Even worse, the install of Windows 7 did something to Grub (Not to anything else in my partition, just Grub).  I can't boot into Ubuntu anymore.

---

### Post by tjwoosta on 2009-01-20
any time you install a copy of windows it will erase grub

its a simple fix..


1. boot live cd

2. open terminal

3. ```
sudo grub
``` 

4.from grub prompt do this
```
find /boot/grub/stage1
```

it will give you something like this (hd0,0) 

5.use the disk that you found with the command above for this next command
```
root (hd0,0)
``` 
(remember to change the numbers to correspond to whatever you got in the previous step)

6.```
setup (hd0)
```  (notice how i left out the ,0)  thats not a typo!

it should give you some type of confirmation that it worked

then you can just quit grub
```
quit
```

then exit the terminal
```
exit
```

reboot!


(you will need to add windows to your /boot/grub/menu.lst)

---

### Post by Achetar on 2009-01-25
ext2ifs doesn't work for me either. 7 x64. nor ext2fsd, or linux fs browser.

---

### Post by fatejudger on 2009-01-26
> **eleifsp said:**
> This hasn't worked for me.  I put the install into both compatibility mode and run as administrator, and whenever I try to open my linux drive (drive X in this case), it asks me to format it.  

Even worse, the install of Windows 7 did something to Grub (Not to anything else in my partition, just Grub).  I can't boot into Ubuntu anymore.

The reason it's asking you to format the drive is because you didn't properly shut down your computer when you last used Ubuntu. That still doesn't address the issue of disappearing drives after reboots though, but at least it's a start.

---

### Post by Achetar on 2009-01-26
@fatejudger: No, I did shut down correctly. And just to make sure, I shutdown properly, rebooted, fscked, then shutdown again, then tried. It said the same thing. BTW it's Mint, not *buntu, but close enough.

---

### Post by withfries2 on 2009-02-01
I'm seeing the same issue: 
[LIST]
[*] Partition of disk into NTFS, EXT3 and swap partitions using Gparted Live
[*]Clean install of Windows 7 Build (32-bit) with Ext2 Installable File System for Windows installed in Windows Vista compatibility mode (into NTFS partition)
[*]Clean install of Ubuntu 8.10 (into ext3 partition)
[*]The EXT3 partition shows up just fine in the IFS Control Panel
[*]When I try to access it, Windows prompts me to format the disk before I use it
[/LIST]

---

### Post by Hugo Bio on 2009-02-03
Yep, i'm having the same issue with Windows7 x64. IFS shows the partition, but whenever i try to access it, windows prompt me to format! :(

Worse thing is, my NTFS partition is only 10 GB (i made it thinking on XP), and fter installing windows 7 (and an antivirus, and adobe reader, and msn live) i have only 19 MB free for using windows. I wish i could move my Documents and settings to my ext3 partition. Otherwise i should backup my stuff and reformat/repartition my whole HDD.

---

### Post by withfries2 on 2009-02-03
I'm thinking about just converting the ext3 partition (which has my /home) into an NTFS partition and letting Linux use the "foreign" file system.

Anyone have success doing that?  Can you do this conversion without reinstalling Ubuntu?

---

### Post by tjwoosta on 2009-02-04
i have used an ntfs partiton for storing my media files before, but often times ubuntu would freeze up when trying to play the files 

i dont think linux gets along with ntfs very well


i could move files back and forth onto the ntfs partition just fine, but if i tried to actually play the files directly from the ntfs partiton it would freeze after about 5 minutes

this leads me to belive that ntfs in linux is not a great idea

i dont know if this is a common issue or not, only that it is an issue that i experienced 


if you do decide to try the conversion, please post back on weather it worked of not

---

### Post by Enyalie on 2009-02-05
> **withfries2 said:**
> I'm seeing the same issue: 
[LIST]
[*] Partition of disk into NTFS, EXT3 and swap partitions using Gparted Live
[*]Clean install of Windows 7 Build (32-bit) with Ext2 Installable File System for Windows installed in Windows Vista compatibility mode (into NTFS partition)
[*]Clean install of Ubuntu 8.10 (into ext3 partition)
[*]The EXT3 partition shows up just fine in the IFS Control Panel
[*]When I try to access it, Windows prompts me to format the disk before I use it
[/LIST]

The problem is that [IFS ]("http://www.fs-driver.org/") doesn't like the 256 inode size that Intrepid formats with. There's a couple solutions out there; I caught the problem before I had a lot of stuff on the partition so I was able simply to reformat using a Hardy cd (which formats with a 128 inode size) and then install Intrepid on the partitions created by the Hardy cd. Looks like there is another solution out there, though. Here are the relevant threads:

[http://ubuntuforums.org/showthread.php?t=1049405]("http://ubuntuforums.org/showthread.php?t=1049405")

[http://ubuntuforums.org/showthread.php?t=979523&]("http://ubuntuforums.org/showthread.php?t=979523&")

---

### Post by wasutton3 on 2009-02-05
i am having the same exact problem. except that i have almost 750 gigs on my tb that i would like windows 7 to access

---

