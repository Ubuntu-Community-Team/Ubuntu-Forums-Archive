---
title: "Unable to boot Ubuntu or Windows--also lost the ability to mount my old Windows"
date: 2016-09-20
forum: Windows
---

### Post by vindor on 2016-09-20
Hi,

I had that awful blue screen of death in Windows.  After being locked out for a while, I sought several solutions, one of which was to migrate to Ubuntu.  I burned the iso, tried Ubuntu, saw that my Windows files were accessible, and decided that while I search the internet for a viable solution, at least I should create an Ubuntu partition in order to continue to do the things I enjoy on my computer.

I didn't know how to uninstall files from my Windows while on Ubuntu, so I only managed to have 41.6 GB of space to create an Ubuntu partition.  I figured I could revisit this later once I managed to fix Windows.  Unfortunately, I slid for the maximum space which seemed to be 41.9 GB.  It was too late before I noticed the difference.  As Ubuntu was being created I wondered if that would cause issues--given that it was more space than available.  I do not know if it had--but somehow I no longer have access to Windows.

Worse, when I try to boot, I get the loading screen for "acer" and it infinitely reboots; so I can't access the Ubuntu partition I created or the old Windows files/command line.

The problem is furthered in the sense that I can not mount the Windows.  So that whole partition sda4 is inaccessible.  And since I can not even boot Windows, the solution offered to help me mount on Ubuntu is out of my understanding.  I.e. I'm told to run "chkdsk /f" in windows but I have no idea how to!

I'm at a loss at what it is I can do.  I partially want to just wipe everything and mount Ubuntu to the whole harddrive--but I have baby pictures, writings, programs, etc I wish to salvage.  I've had some experience with recovering deleted data--but I'm no professional at it--and if it's a gamble which causes me to miss out on so much progress, I would prefer a cleaner way.

Can anyone help?

This is the message I get trying to mount Acer:

"Error mounting /dev/sda4 at /media/ubuntu/Acer: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999" "/dev/sda4" "/media/ubuntu/Acer"' exited with non-zero exit status 13: Failed to load runlist for $MFT/$DATA.
highest_vcn = 0xcac3, last_vcn - 1 = 0x34b3f
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda4': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details."

---

### Post by oldfred on 2016-09-20
Classic Windows fast startup or always on hibernation.
But you have to boot Windows to turn hibernation off. Or repair it when booted directly using f8. Or use the Windows repair/recovery that it wants you to make (most do not).
 Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold) 


 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

Is Acer UEFI boot?
You should then be able to directly boot Windows from UEFI boot menu.

But you will have to set a supervisory password in UEFI and enable trust on the .efi boot files in the ESP.

      
 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392) 
      
 One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details Secure settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL] 

    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by vindor on 2016-09-21
Thank you so much!  You responded so quickly and that eased the frustration of potentially losing all of my data greatly!

I can see now that I have a Windows Problem.  I spent hours trying to repair them--and though I have not made much headway, I was very fortunately able to 'chkdsk' and thus mount Acer in linux.  The big problem is that it appears that much of my data was wiped.

Is there a way to recover that data while using Linux?  At least partially?  I would help for me to 'backup' at least something while I repair this Windows--and hopefully wipe it from my computer!!!

---

### Post by oldfred on 2016-09-21
Best to use Windows repair disk. If you did not make on, see if a friend, work, school has same (64 bit) version of Windows and make a flash drive from that computer.

If partition is still there you can force mount it in Read/Only mode.
If partition is totally damaged testdisk's deeper search or photorec may allow you to recover some data. But Some that use Windows say Windows recovery tools often work better, but may not be free.

       Manual mount read only may work to copy data Have to drill down from computer/system to /mnt.
sudo mount -o ro /dev/sda4 /mnt
May have to create /media/windows mount point first
mount -t ntfs-3g -o ro /dev/sda4 /media/windows 

      
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS

[/URL]
 An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam. 

[URL="http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS"]
[/URL]

---

### Post by vindor on 2016-09-28
Hi!

It's been so long!  I did a little investigating and discovered that--it appears that--when I installed ubuntu larger than I should have, I corrupted the windows partition; and when I ran chkdsk, I created a folder named folder.000 with several folders and 100,000+ files within.  The folders were each named dir.000*.chk and the files were each named file000*.chk where * is any hexagonal number between--I'm guessing--0 and 87CE.

I figure I need to transfer this folder to an external harddrive then clean install an OS.  But while I await the arrival of this harddrive, is there any linux method for recovering .chk files.  Hopefully to their former names but at least to their former file associations.

Attached:
[IMG]http://www.tenforums.com/attachments/bsod-crashes-debugging/103152d1474820951t-can-not-repair-reset-re-install-seems-my-data-wiped-screenshot-2016-09-25-16-26-51.png[/IMG]
[IMG]http://www.tenforums.com/attachments/bsod-crashes-debugging/103153d1474820951t-can-not-repair-reset-re-install-seems-my-data-wiped-screenshot-2016-09-25-16-27-23.png[/IMG]

[IMG]http://www.tenforums.com/attachments/bsod-crashes-debugging/103154d1474820951t-can-not-repair-reset-re-install-seems-my-data-wiped-screenshot-2016-09-25-16-27-44.png[/IMG]

[IMG]http://www.tenforums.com/attachments/bsod-crashes-debugging/103155d1474820951t-can-not-repair-reset-re-install-seems-my-data-wiped-screenshot-2016-09-25-16-27-54.png[/IMG]

[IMG]http://www.tenforums.com/attachments/bsod-crashes-debugging/103156d1474820951t-can-not-repair-reset-re-install-seems-my-data-wiped-screenshot-2016-09-25-16-28-05.png[/IMG]

Also--since I am booting Ubuntu on a flashdrive (as this corrupted Windows blocks me from booting normally)--it appears I can't install anything.

Is there a way around this?  Can I transfer the files, clean install Ubuntu then run a program to reset the associations and names?

How do I install programs despite only being on an Ubuntu trial?

Thanks in advance!

---

### Post by oldfred on 2016-09-28
Please attach screen shots, not everyone has high speed Internet.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Moved to Windows sub-forum as Windows issues.

Do not know how to recover Windows chkdsk files, it may be a case of reinstall and restore from your backups.
Again Windows tools usually are best for Windows and only some Linux tools will work on Windows.

---

### Post by vindor on 2016-09-28
Sorry.  Here are the attachments.  I think.  The instructions seem to be for an earlier forum.

---

