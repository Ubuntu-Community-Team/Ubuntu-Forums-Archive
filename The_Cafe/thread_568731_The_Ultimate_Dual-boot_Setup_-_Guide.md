---
title: "The Ultimate Dual-boot Setup - Guide"
date: 2007-10-06
forum: The Cafe
---

### Post by Mazza558 on 2007-10-06
[SIZE="6"]The Ultimate Dual-Boot Setup![/SIZE]

If you love Ubuntu, but need to keep XP around for whatever reason, such as gaming, specific apps which refuse to run with Wine or in VirtualBox/VMWare, this is the perfect Dual Boot setup.

***Does not work with Vista***

**All you need for this is:**
-Windows XP install CD
-Ubuntu 7.04 and above (as far as I know)
-Internet connection of any kind
-3 or 4 hours of time, at the max. (Usually takes about 2 hours if you're fast)

**Overview**

This setup is at its easiest when starting from clean installs, so if you enjoy your current dualboot setup, there's not really any point in following this guide.

What you are going to attempt is to create 3 partitions (apart from the swap partition), one with Ubuntu on, one with Windows on, and a shared partition. Sounds familiar? Well, how about making the shared partition **ext3**, as well as using it for all Windows software, creating personal folders (like Work, Music, etc), **and** use it as Ubuntu's Home partition? 

Think of the benefits:

-No defragmentation on the shared drive
-Your Windows partition doesn't become defragmented as fast
-The shared partition keeps all your settings for Ubuntu if you want to reinstall
-The two OSs will ignore the files from the other OS unless told to (e.g, Ubuntu will ignore your Program Files folder, and Windows can hide all the Ubuntu system files)
-All your documents and other files are shared, and all programs from both OSs can access them
-Windows programs installed on the shared partition perform a lot faster than on NFTS

Here's a visual idea of what your partitions will look like:

[IMG]http://img248.imageshack.us/img248/2640/overviewhz3.jpg[/IMG]
(Windows Driver letter is actually C:/)

**The Guide** 

**Step 1: Install Windows**

** -Backup EVERYTHING you want to keep!**
 -Insert your Windows XP CD and follow the instructions until you get to the partition menu. Delete all the partitions until you get "Unallocated Space". 
 -Create a new partition for XP to reside in. I recommend to make the size 5-8 GB, depending on the size of your Hard Drive.
 -Follow the instructions and wait for the setup to finish - you should be at the Windows XP desktop.

**Step 2: Set up partitions**

Now we get to the exciting part!

-Grab your Ubuntu CD and slam it into the CD drive. Start to restart XP so that you don't get Ubuntu's Windows menu. 
-Depending on how your PC's set up, it'll either boot straight into Ubuntu or just into XP again. If it boots into XP, restart and look for the key which'll let you access the boot menu.
-When you're in, and you're looking at the Ubuntu LiveCD desktop, you need to find Gparted, the Gnome Partition Editor. In Gusty, this is simply in "Applications > System Tools". 
-Create an ext3 partition to be your shared, and home, partition. Make this very big, but leave some space for the Ubuntu partition. 
-Create another ext3 partition, but this time, use all of the remaining space apart from 1GB for the Swap partition. It's recommended to leave about 15-20GB for Ubuntu if you're an Application Junkie (like me)

**Step 3: Install Ubuntu**

-Hit "Apply" to create your partitions. This could take a few minutes.
-When all is said and done, close Gparted and fire up the installation.
-Follow the questions until you get to the partitioning. Select the **manual** option.
-Select your biggest ext3 partition and click "edit partition". Change the mount point to "/home".
-Select your smallest ext3 partition and click "edit partition". Change the mount point to "/" 
-Tick the "format" option for both of these drives, but **NOT for the NFTS partition!**
-Choose not to import anything from the XP install.
-On the last step, check over the options to make sure everything is in order.
**-Hit Install, and watch those percentages fly!**

**Step 4: Check everything is okay**

-Boot into Ubuntu and check that it boots correctly
-Boot into XP to see if it's still working. Stay on XP!

**Step 5: Setup Windows to recognize your shared partition**

-Install the files required for internet access (if required)
-Point your browser (IE if you have to) to this address:

[http://www.fs-driver.org/download/Ext2IFS_1_10c.exe]("http://www.fs-driver.org/download/Ext2IFS_1_10c.exe")

-Run this program and follow the instructions. You'll find it'll detect both the ext3 partitions. Choose any drive names for the Partitions. It'll then install the kernel extension that allows you to access the partitions from Windows.

**Step 6: Tidy Up**

-Once you have access to your Ext3 Drives from Windows, open the "/home" partition.
-Now, create a folder called "Program Files", and also create another folder called "Documents" (unless you're on Gusty, in which case, this will have already occured)
-Move all your Personal folders into the "Documents" Folder.
-Go to "Start", then right-click on "My Documents". Click on "properties", and change the target for "My Documents" to the Documents folder on your shared partition. Select to move all of the contents of "My Documents" to the new folder. 
-Boot into Ubuntu and change the folder links.

**Step 7: It's Testing time!**

-Grab one of your Windows games or apps to test.
-Choose to install it to your shared partition, in the "Program Files" folder.
-Watch, as it installs swiftly with no hiccups!
-Fire up your newly installed program and watch how quickly it loads and runs!

**Step 8: Enjoy!**

-Sit back and relax! You are now using the Ultimate Dual Boot Setup! :):KS

---

### Post by n3tfury on 2007-10-06
looks like a good guide, but it's been done to death.

---

### Post by Mazza558 on 2007-10-06
> **n3tfury said:**
> looks like a good guide, but it's been done to death.

A lot of people just go for a FAT partition, which fails big-time compared to this.

---

### Post by Mazza558 on 2007-10-06
Anyone else got any thoughts?

---

### Post by n3tfury on 2007-10-06
> **Mazza558 said:**
> Just went through the guide to make sure everything works, and it does :)

lol let me get this straight.  you post a "guide" 7 hours ago where there COULD have been several people finding it and using it and you just *now* know it works?  

i'll steer clear of any of your tutorials, thanks.

---

### Post by Mazza558 on 2007-10-06
> **n3tfury said:**
> lol let me get this straight.  you post a "guide" 7 hours ago where there COULD have been several people finding it and using it and you just *now* know it works?  

i'll steer clear of any of your tutorials, thanks.

Nah, I was just bumping the thread.

---

### Post by angelkiller on 2008-11-13
I just wanted to say that I found this guide very helpful. I successfully followed this guide using 8.10 and XP. Kudos to *Mazza558* for finding such a creative solution.

Now I'd like to mention a caveat I encountered when using Ubuntu 8.10. *Steve1961* explained it to me.
[quote="[Steve1961](http://ubuntuforums.org/showpost.php?p=6158812&postcount=5)"]Since Intrepid the default inode size for ext3 partitions formatted with the Intrepid installer is 256, all previous versions set it at 128. This has caused a few issues, especially with windows based cloning software such as Acronois True Image. If you upgraded an existing installation the inode size will still be 128, but I don't think you can convert from 256 to 128. One option would be the use somethimg like a live gparted or Ubuntu Hardy cd and create and format the partitions with that. Then install Intrepid but ask it not to format the partition.[/quote]
To summarize:
```
8.04 and earlier  -->  OK
8.04 and earlier *upgraded* to 8.10 -->  OK
8.10 regular install --> **Not ok**
```
To get 8.10 working, you must format the partition with anything *except* for 8.10. Then install 8.10 on the previously formatted partition. In sum, don't let Intrepid format the partition.

---

### Post by mehaga on 2008-11-13
Silly. Ubuntu works with NTFS much better than XP does with ext3, no matter how you set it up. I tried everything. Shared partition - NTFS. No headache.

---

### Post by jeremywitt on 2008-11-14
I am going to try this! I beefed while trying to resize my partitions today, so we'll give this a go with all new installs! I'll let you know how it goes. :)

---

### Post by jeremywitt on 2008-11-21
Ok, I got alittle busy and couldn't spend much time on finishing the set up until tonight. Turned out flawless!
I followed the guide to the "T" and also followed angelkiller's advice and used an 8.04 live cd to partition the disk then utilized Ultimate Ubuntu Gamer's Edition as the install.
I would recommend this software and also this guide! Very helpful!

Thank you Mazza558 and Angelkiller!
JeremyWitt

---

### Post by tadcan on 2008-12-11
I've tried this and almost done. Its the simplest things which confuse me to bare with me. 

I've got to stage 6 in the tidy up. I copied all My documents into J:, when I go to the /home folder I don't see the windows one. When I click on properties it tells me 170GB which is the size of the partition I made. 

Can provide screen shots if needed.

---

### Post by Inevitable Glitch on 2009-09-17
> **vekaz said:**
> Silly. Ubuntu works with NTFS much better than XP does with ext3, no matter how you set it up. I tried everything. Shared partition - NTFS. No headache.

I tried this once, problem was that ubuntu wouldn't let me mount /home to an ntfs drive because of something to do with access priveleges.  I'm now trying to make it work with ext2/3, but haven't yet found a way around the inode size problem.

---

### Post by nowin4me on 2009-09-17
Just a warning to everyone it doesn't work with EXT4 :(:(:(:(.

---

### Post by coldReactive on 2009-09-18
Problem: I have to reinstall Ubuntu every time I want to update to a new version, I don't like upgrading through update manager.

This means that I have to remove windows and re-do all of this over again. Windows won't be happy, and won't activate over the Internet after a certain amount of times.

---

### Post by Slug71 on 2009-09-18
I just installed Windows(Vista), then put in the Ubuntu CD and made 4 partitions, FAT32 which is shared and then root, swap and home. If i need to reinstall Ubuntu it doesnt mess with my Windows partition at all and i back up stuff on my shared partition too.

---

### Post by coldReactive on 2009-09-18
> **Slug71 said:**
> I just installed Windows(Vista), then put in the Ubuntu CD and made 4 partitions, FAT32 which is shared and then root, swap and home. If i need to reinstall Ubuntu it doesnt mess with my Windows partition at all and i back up stuff on my shared partition too.

Yeah, but I'd rather use the virtual machine method, much simpler.

---

### Post by serpentine5 on 2009-11-16
I did a google search on duel booting with Ultimate Edition and XP and this thread is what was on the top of the returns.
There are a couple issues I have with it. I see that it was written in 2007 and here it is 2009 almost 2010.... so i know your tut is outdated. I did not check the date of the tut when I started.... 

I have a copy of Ubuntu Ultimate Edition 2.3, and am running XP Pro.
I followed the tut and went to reinstall XP and told the formatter/partitioner to allocate 10gig of a 40 gig HHD to install XP on. Worked fine.
After XP installed totally, I rebooted to the LiveCD, could not find Gparted but I found "Partition Editor" under System>Administration> So I used it. It was a tad bit different than your tut described so I did what I thought was right... 
I took the remaining space, and cut it into three equal pieces because you failed to say anything about the swap area that was shown in the graphic. 
I did the first as:
File System ext3
Label UBHome
Create As: Primary Partition

Second:
File System ext3
Label UBRoot
Create as Primary Partition

Third:
File System ext3
Label SWAP
Create as Primary Partition

Then hit apply. Once it was finished, I hit the install from the desktop and went through the questions until it came to the partition step. I selected "Select Partitions Manually".
I found the HDD I made the partitions on, I selected the first one, and hit Edit partition. Here were a few steps that were not mentioned in your tut either....
First: 
USE AS: Ext3 journaling file system
Format Partition: selected
Mount Point: /home

Second:
Use AS: Ext3 Journaling File System
Format Partition: Selected
Mount Point: /

then I hit next on the installer and it popped up telling me that I did not have a drive selected for SWAP.... This is the step you skipped in the tut, so i hit back and edited the third partition
Third: 
Use As: SWAP AREA 
Would not allow me to select format
Mount Point: unselected (since there was not a SWAP listed in the drop down menu.)

I then finished the install process and rebooted. It booted straight to XP, not to a boot prompt asking me which OS I wanted to boot to or anything.

I have rebooted several times, and everytime it goes straight to XP. I did put the LiveCD back in and booted to it, and it shows that Ubuntu was installed to the drive I partitioned and Mount Pointed as "/", not to the SWAP or the "/home" drives. 

As I am sure you have realized by now, I am not a Linux user... I know my way around a Windoze box, but the ins and outs of Linux/Ubuntu escape me.

Any input that can be provided to help me with where ever I screded up, i would be most thankful.

---

### Post by Annigma on 2009-11-16
Hello serpentine. Welcome to the forums ):P

I can't help you really I'm afraid, but just wanted to suggest that you don't do anything else until someone advises you. 
The reason I say this is that I believe you are not making the best use of your space. The swap partition only needs to be small (it's relative to the size of your RAM), so you're wasting a good few GB there. Also, the maximum number of Primary partitions you can have on a HDD is four, and I think you've used them all up unnecessarily.. Only your Windows 'demands' a Primary partition. Linux isn't so fussy ;) (This will only matter if you want more partitions later. If you're sure you won't, then it doesn't matter.)

I'm sure you're researching whilst awaiting an answer. I am grateful for the help I got recently on [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1321649"), and you may find it helpful.

Good luck. Hope someone comes along soon to help.

:)

---

### Post by pwnst*r on 2009-11-16
> **n3tfury said:**
> looks like a good guide, but it's been done to death.

impostor

---

### Post by serpentine5 on 2009-11-16
Ok, I screwed up farther.... 
After reading several other posts and how to's.... I decided to try the super grub disk.
Downloaded and ran from inside windoze and rebooted. It came up to a prompt, I hit it, it listed several installs of Ubuntu and a windozes install. I selected the first linux, error 15 the second same thing and so on.... so i rebooted and tried it again. the first one allowed me to log into the linux install.... Cool... 
thought I had the issue fixed. So while I was trying to import my windoze settings for firefox, and then my mail folders from my outlook backups... Ifound that I had to go back to windoze to transfer the outlook file to firefox since the linux install of firefox did not have mozilla mail.... So... I rebooted got the grub prompt to select what I wanted to boot to, and when I selected windoze, I now get an error:

Starting up...

NTLDR is missing
Press Ctrl+Alt+Del to restart

Now I dont know what to do.....

I can still log into Linux... but not Windows

---

### Post by serpentine5 on 2009-11-16
ok, i am back to the beginning... I booted off the windoze install disc and went to the repair console... fixed the MBR.... rebooted and it gave me the very first 
grub prompt asking if I wanted to go to windoze or the super grub disc. I chose to boot to windoze and it did... but now I have an exe trying to run at start up, it is asking me before anything else loads to allow unetbtin.exe to run.... no clue what it is.... google search implies it is the uninstaller for super grub disc.

I rebooted from windows, and got the first grub menu, found the linux install, can boot to it but cannot boot to windoze, giving me the same error again....
thinking this is a super grub disc error....

---

