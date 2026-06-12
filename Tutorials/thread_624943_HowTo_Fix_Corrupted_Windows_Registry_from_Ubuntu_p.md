---
title: "HowTo: Fix Corrupted Windows Registry from Ubuntu partition"
date: 2007-11-27
forum: Tutorials
---

### Post by kerrnoPanic on 2007-11-27
I run a dual boot on my work laptop because there are some work related apps that do not run so well 
on my ubuntu partition. :( Anyhow I ran into the dreaded 

[INDENT]Windows XP could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM[/INDENT]

error message. I tried to follow the solution that Microsoft has available on their tech support site, but
was not able to get to the recovery console, not even through the boot cd!!

The steps below are how I fixed the problem! 

[LIST]
[*]**Install NTFS-3G**
[INDENT]This package allows you to perform I/O on an NTFS filesystem.[/INDENT]
[*]**Install NTFSProgs**
[INDENT]This package contains some useful admin tools to use on NTFS filesystems[/INDENT]
[*]**Mount NTFS filesystem**
[INDENT]You will need to mount your Windows partition to backup your corrupted registry files. To do this run the following commands
[INDENT][B]sudo mkdir /media/windows
sudo ntfs-3g -o rw /dev/<device-name> /media/windows
[INDENT]if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount[/INDENT]
sudo ntfs-3g -o force,rw /dev/<device-name> /media/windows

Both of the above commands will mount the device as read-write.
[/B][/INDENT]
[/INDENT]
[*]**Replace these files**
[INDENT]**[COLOR="Red"]You might want to back up the files in /media/windows/WINDOWS/system32/config/ before replacing them just in case this is not a registry problem[/COLOR]**[/INDENT]
[INDENT]Now copy the following files from the file **/media/windows/System Volume Information/_restore{xxx}/RPxxx/snapeshot/** dir:
[INDENT]
_REGISTRY_USER_.DEFAULT
_REGISTRY_MACHINE_SECURITY
_REGISTRY_MACHINE_SOFTWARE
_REGISTRY_MACHINE_SYSTEM
_REGISTRY_MACHINE_SAM
[/INDENT]
to the **/media/windows/WINDOWS/system32/config/** dir and name them as follows:
[INDENT]
_REGISTRY_USER_.DEFAULT            =>  default
_REGISTRY_MACHINE_SECURITY     =>  security
_REGISTRY_MACHINE_SOFTWARE   =>  software
_REGISTRY_MACHINE_SYSTEM         =>  system
_REGISTRY_MACHINE_SAM               =>  sam
[/INDENT]
[/INDENT]
[*]**Schedule a consistency check**
[INDENT]Run this command to schedule a NTFS consistency check for the first boot into Windows
[INDENT]** sudo ntfsfix /dev/<device-name>**[/INDENT]
[/INDENT]
[*]**Reboot into Windows twice**
[INDENT] The first reboot you should get a blue screen telling you that you should run a filesystem consistency check. Let the check run and then the second reboot should bring you back into a bootable Windows[/indent]
[/LIST]

Hope this helps!!

---

### Post by shs123 on 2008-02-17
THANK YOU!

This worked GREAT to get my other partition back!! I was not sure which device had my Windows partition on it, but (after some trial and error) I discovered that it was SDA1. It is nice having that NTFS disk right there on my Ubuntu desk top! I had not used this utility before. I received some kind of "unable to *something*" when I attempted to run the consistency check. I think that my whole issue was a real live corrupt \WINDOWS\SYSTEM32\CONFIG\SYSTEM file since I received an I/O error when attempting to back it up.

I am not sure how to tip your "Thank You" counter on your profile, but please note.. THANK YOU kerrnoPanic!!!

Best Regards,
Sam

---

### Post by Cato2 on 2008-02-26
This looks really useful - there seem to be some typos in a few commands that are missing the 'mount' part:

[INDENT]
sudo **mount** ntfs-3g -o rw /dev/<device-name> /media/windows
sudo **mount**  ntfs-3g -o force,rw /dev/<device-name> /media/windows
[/INDENT]

Also the pathname including 'snapeshot' should be checked as this is a typo.

[INDENT]Now copy the following files from the file **/media/windows/System Volume Information/_restore{xxx}/RPxxx/snapeshot/** dir:
[/INDENT]

---

### Post by Glaxed on 2008-03-04
```

#!/usr/bin/env python
# Try to fix Windows from a Live CD.
import os
os.system("sudo apt-get install ntfs-3g ntfsprogs")
os.system("sudo mkdir /media/windows")
df = os.popen("df -type=ntfs | grep /dev/")
# Rename dev to something safer if you wish (e.g. "/dev/hda1" or "/dev/sda1")
dev = df[1:8]
os.system("sudo ntfs-3g -o rw, force %s /media/windows" % dev)
os.system("cp -r /media/windows/WINDOWS/system32/config/ ~/Desktop")
# I am fuzzy on what /_restore{xxx}/RPxxx/snapeshot/ means.
# If anyone wants to finish or GUI this, you can still use cp to rename files.
# Good luck to all you windows/linux friends out there. :)
os.system("sudo ntfsfix %s" % dev)
print """Hopefully, your Windows disk was mounted and restored.
Will now reboot.
"""
raw_input("Hit any key to continue, or close the terminal to not continue. . . ")
os.system("sudo reboot") 

```
Would it even work?

---

### Post by Cato2 on 2008-03-06
Interesting script, and it could be very useful if enhanced and completed.

However, I recommend it is not actually used yet - it doesn't do any error checking and it's missing the part where you restore the registry from a snapshot (this is the Windows 'System Restore' feature, only implemented under Linux through copying registry files).  

Also it assumes first drive in output from 'df' is the NTFS boot drive (the one with \WINDOWS directory, not one with the MBR boot sector and NTLDR.EXE - Microsoft terminology...) - so it would fail on the Windows PC I'm using where \WINDOWS is on drive D.

It's a lot better, for now, to simply copy and paste the commands into a terminal window.

---

### Post by Glaxed on 2008-03-06
Yeah, it's kinda pointless.
Sorry for bumping, I guess, but this is a great howto.

---

### Post by Stefanie on 2008-05-13
thanks to this howto i fixed my friend's computer yesterday. windows xp didn't boot anymore and the windows xp cd refused to repair his installation, so I used an Ubuntu live cd to restore the files in system32/config . His ntfs partition was detected automatically so i could skip the first three steps. worked like a charm. 
great howto!

---

### Post by tuffguy45 on 2008-11-28
Thanks for the howto, my dad killed our windows computer this morning with a registry "cleaner" program. It wouldn't even boot. Just curious, can you access these files in windows normall? I'm wondering if you could just copy the files from the snapshot dir into the other directory, rename them, and then delete the other files from the command prompt? Having the gui version was a LOT easier but like I said I'm just curious.

---

### Post by Cato2 on 2008-11-29
I think you can copy the relevant snapshot files around from within Windows, but the problem is that the registry is locked when in use (file locking) in Windows.  So it's best to use a Live CD - if you prefer a GUI, just use the Ubuntu Live CD and use the Nautilus explorer tool to copy files around.

As always, you REALLY need to back up registry files onto a USB stick or similar before you start deleting or overwriting them...

---

### Post by Drumplayr on 2009-06-17
Still works great. I used Ubuntu 8.1 live CD and didn't have to install anything. I just had to mount the Windows partition manually.
Also, before running ntfsfix, I had to unmount the Windows partition.

Thanks,

Drumplayr

---

### Post by bsmith1051 on 2009-06-18
BY FAR the most common problem on Windows machines is a bad sector developing in one of the registry files.  If you don't have a usable backup of same then you're hosed no matter what else you do.

So I would suggest a slight variation on the procedure:

1. mount the drive from Ubuntu (see details above)

2. try to copy all the registry files from "\windows\system\config" to someplace/anyplace else.  If one of them fails to copy then you know which file needs to be replaced; if none of them fail then maybe the ntfsfix is all you need.

3. *IF* the Windows machine had System Restore enabled then you'll be able to find a backup of the registry files in one of the "\windows\System Volume Information" sub-folders.  Otherwise, you can also try the folder, "\windows\system32\repair", which always has a backup (though by default it's only the initial most-basic version; I run NTBACKUP on every Windows machine I touch so as to update this 'repair' backup)

4. try to rename the damaged file, i.e., leave it in-place but unused.

5. copy the backup of the damaged file to the "\windows\system32\config" folder

6. run 'ntfsfix' (to trigger the built-in Windows Check Disk on next boot) 

7. reboot the machine
8. cross fingers

---

### Post by zah_zaf on 2009-06-26
Here is my short story:

When I boot into Ubuntu Live mode through a USB boot and run **sudo fdisk -l **all I see is the usb device /dev/sdb with the /dev/sdb1 and I dont see /dev/sda ... Also, while its booting into live mode I see some error msgs regarding /dev/sda - disk error.

Is my internal drive hosed ?

Long story:

1. When I boot up directly into Windows (my laptop is a X61 tablet - no CD drive) I can see the Windows logo appear and then the progress bar ... and then before I get the logon option I get the error msg saying sytem32/config/SYSTEM is corrupted, insert Win Xp CD and run repair.

2. Since I dont have a CD drive on my laptop I create a USB bootable ubuntu 9.04 using **uSbuntu Live Creator **(ofcourse I have another machine to do this) to fix the file corruption problem

3. USB bootable created and I am getting ready to replace all the corrupted files and then I run into missing /dev/sda problem.

I dont think it is an NTFS mounting problem, becuase I tried this on another laptop with Windows running fine and an NTFS partition and this cleanly showed up as an "Internal Drive" in  Nautilus

The only silver lining is that, atleast when I try booting directly into Windows  it doesnt blow up in my face saying Internal Disk Failure and proceeds until a certain point. What baffles me is that there are /dev/sda error msgs and the /dev/sda doesnt show up during the USB boot. Unable to proceed after this. Anbody with a rescue plan?

Thanks,

zah_zaf

---

### Post by Cato2 on 2009-06-28
Drumplayr - Good to hear that it still works well.  It would be great if someone turned this into more of a point and click application, though.  

Has anybody tried this on Windows 7 registry, by the way?  I've been too busy to do much with my beta of Win7.

---

### Post by Cato2 on 2009-06-28
Hi bsmith1051,  Good point about file/disk corruption, although this isn't always the case so your steps are an add-on if you suspect corruption.

In step 2, I'd suggest you copy the registry files with gddrescue (GNU ddrescue - in the Ubuntu repositories, but avoid the non-GNU version which is not as good).  This is great at recovering as much as possible of a corrupted file (or disk), and also isolates which if any parts of the file/disk cannot be read.  Unlike a normal cp or dd command, it will not give up on the first error.

Registry files recovered by gddrescue should not be used for normal operations but they might be useful in recovering specific reg keys.  Generally it will be quicker and easier to go back to an earlier registry version using System Restore, though.

---

### Post by Cato2 on 2009-06-28
Hi zah_zaf,

You need to go into the log files on your Ubuntu live CD.  In terminal, type "less /var/log/messages" and read through from the time of boot, looking for any errors to do with /dev/sda, IDE, ATA, SATA, etc.  It certainly looks as if your disk has problems.

Try GNU ddrescue as mentioned on my previous posts - "apt-get install gddrescue" should install it for you - as it will give possibly better error messages.  If you can connect a big enough USB external drive, you should

1. Copy your entire disk (/dev/sda or whatever) onto the external drive - you can copy it into one huge file if the external drive is big enough.

2. Recover this disk on another system (or use this system if necessary, with a live CD).  Google for Linux disk recovery, SystemRescueCD, and hard disk recovery - there are a lot of resources out there.

Good luck.

---

### Post by bcboybuzz on 2009-08-01
First up, thank you OP and all contributors, you really saved my bacon there! I was all smiles and 'I am a Genius! I can fix a Windows crash in Ubuntu!' when I was finished...

Couple small tidbits I'd like to add.

First, I'm running Vista Premium 64 [and Ubuntu 9.04 64] on a homebuilt gamer's wet dream. I'm not trying to brag, and since they don't matter, forget the specs. The point is, some files are not in the same place. 

As I read point #3 in bsmith1051's post, I came to realize that getting rid of my shadow copies and restore points to free up space wasn't such a great idea after all... To make matters worse, "\windows\system32\repair" didn't exist. After a few moments of cold-sweats, and then some poking around, I found them tucked away in '**/Windows/System32/config/RegBack**' Dunno if its a Vista thing or a x64 thing, but that's where they were on mine.

Point two: ddrescue needs some batch process ability. I suppose I could write a script for that, but I haven't got that far into the Linux-for-ex-Windows-users book... I suppose it's no more complicated than the old .BAT files from the good ol' DOS days... 

In the end, since I had tried to copy the /config folder out as a first step [failed, file SYSTEM was about 4 megs smaller than the original, not to mention some missing .LOG files, which I assume were after SYSTEM in the copy queue], I just renamed the corrupt file and copied in the backup, ran ntfsfix [ps you gotta umount before you can ntfsfix: **sudo umount /dev/sda1 && sudo ntfsfix /dev/sda1** is the command if it's still mounted from ntfs-3g; can't use Gnome to do it], restarted and started celebrating.

Thanks again. A gamer's computer is just not the same with Linux. Though I actually spend more time in my Linux environment than I do the Windows one now. Too bad COD and Fallout 3 and GRID and all the rest weren't Linux-compatible...No money in a free OS, I guess...

---

### Post by macbraughton on 2009-09-02
I just purchased a 1005HA Eee PC with XP pre-installed.  I tried a copy of Ubuntu Netbook Remix first and then put in Linux Mint which is what is currently installed in a dual-boot set-up.

I've been waiting to buy a netbook for a long time, hoping that the ARM platform ones coming with Linux pre-installed would finally get here but it seems to be drawing on longer and longer.  

Anyway, the only reason I got this one is because I have a single program that I can't live without that only runs in Windows and I figured that if I was going to have to pay MS $100 just to run a virtual version, I might as well spend $400 and get a whole computer (think also, of course, I can dual-boot with my favorite Linux distro).

My wife booted XP Home Edition up earlier today and it gave the:

> Windows XP could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM

error.

I found this page by typing "fix windows registry from linux" in google, and this was the first hit.

I was able to mount the Windows partition following the instructions in this post without having to install anything.

I was able to move and rename the files as well.

The only problem I had was executing the command for the consistency check because of some permissions issue (which the computer ran automatically after the second reboot anyway).

This is one of the simplest and most useful fixes I have ever found, and I am extremely grateful to kerrnoPanic for posting it.

In my initial research the other ways of fixing this problem inevitably involved using Windows software on a computer with Windows installed on it already (which I am unable to do because I own no other computers with Windows), and I find it ironic that it appears to be much easier to fix these sorts of problems in Windows using Linux than it does within Windows itself.

Again, thanks, and I just want to point out that I was also able to mount the Windows partition of the HDD from the live version of Linux Mint on a USB stick.  I hadn't found this post yet so I didn't know that all I had to do was move a few files.  That being said, I think it would be entirely feasible for somebody to fix a Windows computer with a live version of Linux regardless of whether or not Linux was already on it or not.  Pretty cool!

---

### Post by chris.flesher on 2009-09-29
Thank you so much! This saved my *** today big time.

---

### Post by tturrisi on 2009-10-01
Bear in mind that this solution only works IF System Restore is enabled in Windows, else the restore points do not exist here:
System Volume Information/_restore{xxx}/RPxxx/snapeshot/
nor do they exist anywhere else.

---

### Post by kevinguillorytraining on 2009-10-09
THANK YOU for nice tutorial.

---

### Post by GlobalTrucker on 2010-01-21
Here is a slightly strange but related question. My apologise that I start off talking about Windows but nobody is perfect!!
 
Background:
 
[I][COLOR=darkorchid]"OS: Windows 7 Home Premium OA

Start up and installation worked first round. I then made the following partitions:

C:Windows (original system partition)
D: Data (here I put all my working files)
F: Executables (here are all the binary executables that I use)

I moved some files from C:\Programs to F:\Programs.

Everything worked fine.

Then I got clever and decided to change F:Executables to E:Executables (E for Executables) to do this I had to move E:DVD (original system default) to a new letter. I chose O:DVD (O for 'Optical') and moved F: to E:.

Then I re-booted.

Now the system boots all the way to the login screen except that there are no user choices. Windows itself has obviously started because other functions such as the 'Shutdown' and 'Restart' buttons work. But no User icons or boxes appear to select a user and enter a password."
[/COLOR][/I]
At this point I thought "DAMN and double BLAST!"
 
After a bit of cursing and thinking (these often work well together) I had the idea to see what my (up until this point unused UBUNTU boot disk could do. In it went to the optical drive and started up a dream. In fact I had access to all the WIndows partitions as well. However, I can't seem to get windows applications to run under UBUNTU yet (mostly because I haven't tried very hard).
 
I suspect that the problem with my Windows installation is that I need to fix some drive pointers in the windows registery file. Unfortunately the 'regedit' utility doesn't want to work directly under UBUNTO. When I double click on it in the file manager it complains that it must be some kind of corrupted *.zip file. Most unsatisfactory.
 
After this very long post the basic question is:
 
Can I open up and edit the windows registry file directly from UBUNTU?

or

Any other ideas?

---

### Post by Mickser_52 on 2010-01-26
Many thanks for your post. My daughters laptop contracted a windows logon logoff virus after opening an email attachment (yes, despite all those warnings). Every time she tried to start up, as soon as she entered her password the system logged off.

I was able to boot up from an ubuntu disk and download and run an antivirus program (bitdefender) which cleared the original virus but the windows would still not stay logged on.

I found your post and followed your instructions to replace the files as suggested. The problem was solved:D

---

### Post by suniyo on 2010-02-08
Great!! Simply worked out of the box and now I've my partition recovered without needing to install either windows or ubuntu again. Very old and yet very useful information. I think there are lot many such problems that we need to address and properly document for other users also. Anyone interested working with me to document ?

---

### Post by singh9211 on 2010-02-09
thanks for the gr8 tutorial, it really helped

---

### Post by suniyo on 2010-02-14
Instructions are very old but still today they work like charm. Solved my problem this way and now windows is working well too. I think we need a proper guide for this kind of problems @ ubuntuforums. 

Many thanks for providing this superb solution, it saved my butt, literally.. :)

---

### Post by Detonate on 2010-02-14
I wish I had seen this thread earlier.  It would have saved me a lot of work.  I have copied the entire thread to my computer for future reference.

Thank you very much.

---

### Post by toast_kid on 2010-02-21
Hi
 
I just wanted to say thanks for posting this... you saved me a rebuild!
 
Cheers

---

### Post by the_flying_os on 2010-07-09
i'm having trouble understanding [B]sudo ntfsfix /dev/<device-name> 

[/B]what do i put in for 'device name'? I put in the name of my hdd and i get:

ubuntu@ubuntu:~$ sudo ntfsfix /media/SQ003938
Mounting volume... Error opening partition device: Is a directory.
Failed to startup volume: Is a directory.
FAILED

---

### Post by Cato2 on 2010-07-10
> **the_flying_os said:**
> i'm having trouble understanding [B]sudo ntfsfix /dev/<device-name> 

[/B]what do i put in for 'device name'? I put in the name of my hdd and i get:

ubuntu@ubuntu:~$ sudo ntfsfix /media/SQ003938
Mounting volume... Error opening partition device: Is a directory.
Failed to startup volume: Is a directory.
FAILED

The /media/SQ003938 is not your device name, it's a "mount point" (like a drive letter in Windows, sort of) - you could mount the same disk partition in several places on the Linux filesystem hierarchy (e.g. /tmp/fred, /media/usb_drive, /media/mydrive, etc).  See [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount) for more explanation of the concepts.  Device names in Linux always start with /dev, e.g. /dev/sda1.

Since your disk partition was already 'mounted' by Ubuntu, you can just type this into the command line shell: ```
df -h
``` (shows disk free space) or ```
mount
``` - find the line corresponding to your /media/SQ003938 and read out the device name.

For example, here the /backup line is the mount point for /dev/sda5:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.3G  3.2G  5.7G  37% /
varrun                247M  420K  246M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M   44K  247M   1% /dev
devshm                247M     0  247M   0% /dev/shm
/dev/sda1             228M  104M  113M  48% /boot
/dev/sda5             683G  518G  138G  80% /backup

```

Good luck with the recovery.  

Incidentally the link by 'Emilyroggers' above is for commercial software that runs on Windows, and not much use if your PC is unbootable.

I had a bad block in the Windows registry on a laptop recently, which stopped me booting the PC.  I would have used Ubuntu and GNU ddrescue to recover the whole disk if only my IT department didn't mandate the disk is encrypted - this technique of using an Ubuntu live CD only works with unencrypted disks (unless you use TrueCrypt perhaps).  See [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) for help with recovering hard disks on Ubuntu, including use of GNU ddrescue (package is 'gddrescue' on Ubuntu, not 'ddrescue' which is a different and less complete program).

---

### Post by melnichuk on 2010-07-11
Nice tutorial, thank you. But what should a user do on a Windows machine if System restore points creation is turned off? In such a  case your System Volume Information/_restore{xxx} folder will be empty.
In connection with the Windows viruses and impossibility to start **regedit** or Windows in whole, sometimes Windows users need to edit the registry from outside. I've found, so far, the only utility in Linux **chntpw**, which was originally designed to reset passwords, and then acquired the registry editing ability. 

**Editing the registry:** 

1. Boot from a LiveCD or install a second system Ubuntu.

2. Install **chntpw** utility:

```
sudo aptitude install chntpw 
```

3. Mount Windows partition: 

Find the Windows partition: 

```
$ sudo fdisk -l
```

Assume it is on /dev/sda2. Next step is mounting of the partiotion:
 
```
$ sudo mkdir /media/windows 
$ sudo mount /dev/sda2 /media/windows
```

4. Registry editing

```
$ chntpw -l /media/windows/Windows/system32/config/software
```

Move to registry branch you need, for example: 

```
$ cd Microsoft\Windows NT\CurrentVersion\Winlogon
```

and edit a key, for example:
 
```
$ ed Shell 
```

**Password resetting: **

1. See 1-3 of the previous section 

4. Find the user whose password will be changed 

**$ chntpw -l /media/windows/Windows/system32/config/SAM**

5. Password resetting 

```
$ chntpw /media/windows/Windows/system32/config/SAM -u Administrator
``` 

Just cite the places in the registry where they can hide a record of running viruses: 

HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Notify 
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Userinit 
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\Shell 
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run HKLM\SOFTWARE\Microsoft\Active Setup\Installed Components 
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\SharedTaskScheduler 
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\ShellServiceObjectDelayLoad 
HKCU\Software\Microsoft\Windows\CurrentVersion\Run 

The default values in Regedit: 
[HKLM\Software\Microsoft\Windows NT\CurrentVersion\Winlogon] 
"Shell" = "Explorer.exe" 
"Userinit" = "C:\WINDOWS\system32\userinit.exe" 

Check the Explorer.exe file to the presence of double ... the right place for the file is Windows\ but not Windows\System32\ ...

---

### Post by ZenStephanie on 2010-07-31
Thank you, thank you, thank you to the OP of this thread.

My Windows machine crashed and I could not get Windows back up and running after numerous attempts. I was able to use testdisk to do some repair of the Windows boot sector, but this fix is what ultimately got me back in.

Once again: THANKS!!

---

### Post by wonderl on 2010-08-08
@[melnichuk]("http://ubuntuforums.org/member.php?u=587385"):  Thanks a lot for your little tutorial! With "delallv" (delete all  values) and "dk" (delete key) i was able to delete the malicious key  "\Microsoft\Windows NT\CurrentVersion\Image File Execution  Options\userinit.exe". For making this key-removal persistent, I had to  use chntpw with the "-e" option, i.e.: [FONT=monospace]
[/FONT]
 ```
$ chntpw -e /media/windows/Windows/system32/config/software

$ cd \Microsoft\Windows NT\CurrentVersion\Image File Execution Options\userinit.exe

$ delallv

$ cd ..

$ dk userinit.exe

$ q
```[FONT=monospace]After quitting ("q"-command) I chose "y" to write back the registry change.

Here is some info on how to use chntpw: [http://pogostick.net/~pnh/ntpasswd/regedit.txt]("http://pogostick.net/%7Epnh/ntpasswd/regedit.txt")

Thanks and Regards,
wonderl

[/FONT]

---

### Post by sstvinc2 on 2010-08-30
Great how-to.  Just wanted to give a bump to keep this around.  Just used it to perfection.  I did run into trouble unmounting the windows disk and running ntfsfix, but it didn't even matter.  Everything booted just fine.

---

### Post by tcdoe on 2010-09-02
wow.
thanks SO MUCH.

i had this problem and tried practically every solution. almost gave up and reformatted. but then saw your post and it worked.

the only difference was that the ntfsfix step wouldn't work because im running a WUBI ubuntu and the disk is not 'unmountable' and couldn't set the fix.

still, your solution worked and i was able to boot into windows and now i'm running a chkdsk /r and it's finding lots of problems but looks ok.

again,
thx,
t.

---

### Post by anantha89 on 2010-10-24
> **kerrnoPanic said:**
> I run a dual boot on my work laptop because there are some work related apps that do not run so well 
on my ubuntu partition. :( Anyhow I ran into the dreaded 

[INDENT]Windows XP could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM[/INDENT]

error message. I tried to follow the solution that Microsoft has available on their tech support site, but
was not able to get to the recovery console, not even through the boot cd!!

The steps below are how I fixed the problem! 

[LIST]
[*]**Install NTFS-3G**
[INDENT]This package allows you to perform I/O on an NTFS filesystem.[/INDENT]
[*]**Install NTFSProgs**
[INDENT]This package contains some useful admin tools to use on NTFS filesystems[/INDENT]
[*]**Mount NTFS filesystem**
[INDENT]You will need to mount your Windows partition to backup your corrupted registry files. To do this run the following commands
[INDENT][B]sudo mkdir /media/windows
sudo ntfs-3g -o rw /dev/<device-name> /media/windows
[INDENT]if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount[/INDENT]
sudo ntfs-3g -o force,rw /dev/<device-name> /media/windows

Both of the above commands will mount the device as read-write.
[/B][/INDENT]
[/INDENT]
[*]**Replace these files**
[INDENT]**[COLOR="Red"]You might want to back up the files in /media/windows/WINDOWS/system32/config/ before replacing them just in case this is not a registry problem[/COLOR]**[/INDENT]
[INDENT]Now copy the following files from the file **/media/windows/System Volume Information/_restore{xxx}/RPxxx/snapeshot/** dir:
[INDENT]
_REGISTRY_USER_.DEFAULT
_REGISTRY_MACHINE_SECURITY
_REGISTRY_MACHINE_SOFTWARE
_REGISTRY_MACHINE_SYSTEM
_REGISTRY_MACHINE_SAM
[/INDENT]
to the **/media/windows/WINDOWS/system32/config/** dir and name them as follows:
[INDENT]
_REGISTRY_USER_.DEFAULT            =>  default
_REGISTRY_MACHINE_SECURITY     =>  security
_REGISTRY_MACHINE_SOFTWARE   =>  software
_REGISTRY_MACHINE_SYSTEM         =>  system
_REGISTRY_MACHINE_SAM               =>  sam
[/INDENT]
[/INDENT]
[*]**Schedule a consistency check**
[INDENT]Run this command to schedule a NTFS consistency check for the first boot into Windows
[INDENT]** sudo ntfsfix /dev/<device-name>**[/INDENT]
[/INDENT]
[*]**Reboot into Windows twice**
[INDENT] The first reboot you should get a blue screen telling you that you should run a filesystem consistency check. Let the check run and then the second reboot should bring you back into a bootable Windows[/indent]
[/LIST]

Hope this helps!!
Thanks a lot.... :)

---

### Post by Stop Being Such a TOONA on 2011-02-16
I love you

---

### Post by PcPro12 on 2011-04-06
Great tutorial. However, I got one question. If your computer has been used for months in a row with lots of software on it and you replace the "SOFTWARE" file in the register, you just erased your entire history of installed and working programs and I think the drivers as well, or they may be in the "SYSTEM" file or any other, I'm not sure about that one. 

But anyway, my dad has a friend who has this exact problem and I used this method to fix it and the system started and ran like normal, except that firefox, malwarebytes, and any other program wouldn't work anymore, not even internet explorer and all drivers were gone. No display driver, no ethernet or wireless driver, no nothing.

The problem with this laptop is in the "SOFTWARE" file, so I might as well leave everything else alone, but is there a way to repair the problem without having to replace the file? Can I edit the file and remove something? the error code is **STOP: C0000218.**

P.S. Sorry for reviving an old topic, but this is right on with my problem, so I decided to post here, if no one minds? :)

Thanks,
PcPro12

---

### Post by bsmith1051 on 2011-04-07
You should be glad you got his copy of Windows up-and-running again, at all.  Can't you just re-run the installers for those apps?

As for alternate forms of repair, you didn't really give us much to go on -- and you should ask for Windows repair advice on a Windows forum, not here.

---

### Post by chief_wrench on 2011-08-31
just registered to let you know: works like a charm. made a friend of mine VERY happy.

---

### Post by Pott on 2013-06-20
Thanks so much for this! If that's ok I have a few questions (and sorry for zombie threading). This is the current situation
1) Can't even boot into windows, due to a corrupt registry
2) I can boot from Ubuntu on a USB-drive
3) I could not boot from a Windows recovery CD

I tried using this guide, however Ubuntu did not find NTFSProgs to install, and I also was not able to use the ntfs-3g command (''Failed to access volume '/dev/sdb/media/windows': Not a directory'')
I may have identified my drive device incorrectly though... Command run: ```
sudo ntfs-3g -o rw /dev/sdb/media/windows
```

Furthermore, when I use Nautilus to navigate into system volume information, there are no files in it.

Am I such a noob that I missed something obvious here? Is this method what could revive my beloved PC?

Ironically I don't download anything and never had a virus in my life... :( I've no idea how this happened.

---

### Post by frank.a.silva on 2013-11-05
Thanks!!  This solution still works.  I had to fix a roommate's XP work computer and followed the instructions with a few minor adjustments.  Here are my notes:


[LIST]
[*]Download latest **desktop **version of Ubuntu ISO
[*]Create bootable CD or USB thumb drive
[LIST]
[*]UNetbootin is a good utility for creating bootable USB drives for many different Operating Systems and Utilities)
[*][http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[/LIST]

[*]When booting from Ubuntu, steps 1, 2, and 3 are pretty much already done
[LIST]
[*]NTFS-3G is already installed
[*]NTFSProgs is now included in NTFS-3G and doesn't need to be installed
[*]NTFS filesysystem is generally already mounted
[/LIST]

[*]For step 4, it's probably best to copy a backup of the files to another USB drive or a network drive
[*]before running the ntfsfix command you have to unmount the Windows drive
[*]After the first reboot, it went automatically into windows without doing any system checks.  However, after rebooting it did do a file system consistency check.  I did a 3rd reboot just to make sure everything worked.
[/LIST]

Regards,

Frank

---

### Post by chitreddysandeep on 2014-09-06
Thank u Kerrnopanic. Ur solution worked fine to me. For layman Identifying devicename of windows is a little troublesome. My answer to them is use GParted Partition editor.It will list all partitions. There is an  issue during the NTFS consistency check.

command: ntfsfix /dev/sda1
Issue:       Refusing to operate on read-write mounted device /dev/sda1.

Solution:   Try unmounting the drive first - running this program on a mounted drive apparently doesn't work -
               sudo umount /dev/sda1
               ntfsfix /dev/sda1

PS: sda1 is where my windows installed, it might vary for others.

---

