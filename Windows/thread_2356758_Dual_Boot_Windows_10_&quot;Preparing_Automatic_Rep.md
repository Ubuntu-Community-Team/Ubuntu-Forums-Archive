---
title: "Dual Boot Windows 10 &quot;Preparing Automatic Repair&quot;"
date: 2017-03-26
forum: Windows
---

### Post by figytuna on 2017-03-26
Hello,

I need help recovering files from the Windows side of my machine which won't boot. Here is the story:

**-Before the problem:**

I've been successfully running dual boot Ubuntu 16.04 LTS and Windows 10 on my ASUS Laptop ( [X550DP]("https://www.asus.com/Notebooks/X550DP/") ) and I have been able to switch between the two without trouble for a few months. Although the time has always been wrong on the Windows side, as well as a disk usage issue also on the Windows side which I will get into, no other problems were present.

**-How it happened:**

The other day I started Windows and it was running unusually slow. I was only able to open a file explorer and the task manager before I realized that it wasn't just because the computer had just started up. The task manager said the disk usage was at 100% even though no process was using more than 0.1 mbs. (This seems to have been a problem with this laptop and Windows, I've had to replace an old hard drive because of it but lately it's been able to get out of this state shortly after startup. **Also, disk usage has never been a problem while running Ubuntu**)

After that I got a dialogue box saying something like "This process is running slow, would you like to end it?" (I can't remember exactly what it said). I said No at first because I only had file explorer and task manager up and it seemed to be talking about the file explorer. The computer was still stuck though and the dialogue came back and this time I said Yes. The start menu, background image and file explorer all disappeared and all that was left was the task manager on a blank screen. I left it for a while before finally hard powering it off (I knew I was going to have problems after that).

[B]-Current state:
[/B]
Now, I am still able to boot into Ubuntu with no problem. **Whenever I boot into Windows, it says "Preparing Automatic Repair" and then goes to a black screen**. It's also important to note that all I care about is retrieving certain files from the windows side, no programs or anything.

[B]-Things I've Tried:
[/B]
I've tried repeatedly hitting F8 while booting into Windows, Shift+F8, running my finger across F1-F12 and hitting shift like a mad man. No menu comes up, it always tries to do automatic repair then goes to a black screen forever.

I've tried mounting the nfts file systems from the Ubuntu side and get this error:
```
Unable to access “87 GB Volume”

Error mounting /dev/sda4 at /media/ryan/DAE826D9E826B3A3: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda4" "/media/ryan/DAE826D9E826B3A3"' exited with non-zero exit status 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

I've tried running nftsfix which doesn't seem to do anything (and maybe isn't what I want according to other forum posts)

I've tried looking at the partitions in GParted and there is a red exclamation mark by two of the Windows related partitions. For "Microsoft reserved partition" it says:

```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda3 is missing
```

and for "Basic data partition" (which is sda4, the main, large partition where my files are) says:

```
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ntfs file system support:  ntfs-3g / ntfsprogs.
```

I've tried downloading a Windows 10 recovery image, putting it on a flash drive and booting from it. It's actually a Windows 10 installer but I thought it might be the right thing. Regardless, when I try booting from it (both by switching the boot order and chosing it from boot override) It shows the ASUS logo like it does when it says preparing automatic repair but does not say that this time, but it still goes to the same black screen and gets stuck.

Finally, I've tried using testdisk. after doing a quick search, I have it do a deeper search on the Windows stuff and it only gets a little ways before getting stuck and slowing Ubuntu down to a crawl. After a few minutes it says something about a problem and tries to proceed, still slowing Ubuntu. After about half an hour of no progress I slowly shut it down. I waited for it to stop everything properly and shut down Ubuntu normally, but it took 5ish minutes because things were still slow. When I tried to start Ubuntu back up there was a filesystem error and it put me in busybox and told me to run fsck. I did that and it went through and fixed a bunch of things and was able to start Ubuntu again. However that was all Ubuntu, Windows still doesn't work. And I'm afraid of using testdisk now.



Any help would be appreciated, again, I don't want to save all of Windows, I just want to copy some important files to somewhere safe, after that I could wipe the whole computer if need be.

---

### Post by Geoffrey_Arndt on 2017-03-26
Others here at Ubuntu Forums will have to contribute more info, but, I would suggest you only work from a LIVE linux (either the Ubuntu install media, or download "Parted Magic", burn it to CD or usb-stick).    Parted Magic has several tools installed to do data rescue.   Note that Parted Magic is not totally free . . but at $9.00 for the install iso, it's worth it to me - - so for you, it's just another option or tool in your toolbox.    No need to run Ubuntu from the installed OS to do this type of work.

[https://partedmagic.com/](https://partedmagic.com/)

---

### Post by figytuna on 2017-03-27
Thanks for the tip. Now that you say it, it makes a lot of sense to stay off the Ubuntu instance which shares a hard drive with the data I'm trying to save. It just seemed so convenient but really may just be asking for trouble.

---

### Post by oldfred on 2017-03-27
Moved to Windows sub-forum, since Windows issues.

The Linux ntfsfix does very little and turns on the Windows chkdsk flag so Windows boot will repair run the chkdsk.

The Linux NTFS driver will not auto mount Windows partition that are either hibernated or need chkdsk. So once you turn on chkdsk flag with ntfsfix you cannot mount it read/write. Sometimes you can manually mount read-only.

Often grub boots into Windows too fast to get into f8 repair console. Some have said multiple tries and almost same time as pressing entry in grub may work.

If BIOS Windows system you may be able to temporarily install Windows boot loader and get into Windows internal repair console. IF UEFI you should be able to directly boot from UEFI boot menu.
Best to have Windows repair disk or installer with repair console to fix Windows. 
And have available current version repair disk or Ubuntu installer for every operating system you have installed.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL]
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 

      
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085) 
   Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by missmoondog on 2017-03-27
on my 1 machine that i dual boot, there have been 2 times that after a windows update, i've had to run chkdsk to fix boot up issues. both times i did that it correctly fixed the issue. it only did the quick chkdsk so it didn't very long to fix.

i also did repair grub in the advanced options when starting up computer for a friend 1 time and that worked also, but took and extra restart to totally start correctly.

---

### Post by figytuna on 2017-03-27
Thanks for the help.

I tried getting into the F8 menu again, I've tried pressing F8 repeatedly while choosing Windows Boot Manager and I've tried it while holding shift, holding both, etc... It doesn't seem to work but maybe I'm just unlucky.
I keep trying to boot a Windows repair USB, I should be able to because I select it from the boot options (UEFI) but it still just shows up as a black screen.

Thanks for all the information oldfred, I still haven't gone through all of your links extensively but I'll post another reply if I get something to work.

---

### Post by oldfred on 2017-03-28
Do not know Windows well enough to offer much more.

My one Windows system is just to watch TV and any fixes I do to it, I have to open all my links to find commands. And I swear menus are not the same. And rarely does anyone post the commands that Windows could use in its terminal. I had Windows as even all the available help does not seem to help.

But I do have multiple backups & repair flash drives for my one Windows system.

---

