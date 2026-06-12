---
title: "cant mount a hdd or see the partition that i need to recover"
date: 2019-06-21
forum: Windows
---

### Post by amd1250 on 2019-06-21
i have a hard disk hooked to my laptop one day i got back from work  to see it wont boot had windows installed on it tried accessing it from another computer  using windows it reads there is a hdd in windows manager but nothing  shows up in file explorer i heard from a friend i can use ubuntu from a usb stick and try to  access the hard disk from the os  did that on a different laptop and successfully booted to ubuntu using  "try without installing" when i try to access my plugged hard disk using a sata to usb dongle i  get the following 
[URL="https://drive.google.com/open?id=1qHoWMIHTtd4whITR7RE2quTHb26ZBaIJ"]https://drive.google.com/open?id=1qHoWMIHTtd4whITR7RE2quTHb26ZBaIJ
[/URL]

  i tried to get a list of hard disks connected to the laptop it shows up using only the command line  "sudo lshw -class disk -short"
  [https://drive.google.com/open?id=1jvmCR8NPLKPTu3FLOfY4svHTln_MWnnn](https://drive.google.com/open?id=1jvmCR8NPLKPTu3FLOfY4svHTln_MWnnn)
 it shows there that my hard disk 

  tried to pinpoint the correct partition but no other command work  idk why and i have 0% knowledge as how to know the correct partition to  mount it to directory so i can access the hard and get my files back 
  [https://drive.google.com/open?id=1vllaqExQrwdWtrZxLzdp1C1bgTdgmiOW](https://drive.google.com/open?id=1vllaqExQrwdWtrZxLzdp1C1bgTdgmiOW)

---

### Post by oldfred on 2019-06-21
Since Windows, moved to Windows sub-forum.

The commands for fdisk & parted use -l, that is dash lower case el, L not 1 (one) or cap I.
sudo parted -l
sudo fdisk -l

Windows normal shutdown uses fast start up which sets the hibernation flag. The Linux NTFS driver will not default mount a hibernated NTFS partition to prevent damage. You may be able to force mount in read only mode.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If not hibernation flag, NTFS may need chkdsk or other repairs. Those cannot be done from Linux, but only from your Windows or a Windows repair disk.
       
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    
        
 Force mount, read only (ro), change example with sda3 to your correct NTFS partition:
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sda3 /media/windows

---

### Post by The Cog on 2019-06-21
Well, I'm not convinced this post should have been moved to Windows just because it's an ntfs disk, but never mind.

I assume the disk you are trying to read is /dev/sdd - the one you plugged in partway through (earlier lshw didn't list it). 
Replace sda3 in  the instructions that oldfred gave you with sdd5 (guessing based on the first error popup you posted):
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g -o ro /dev/sdd5 /media/windows
```
However, the IO errors worry me. I think the disk may have developed a fault and be basically unusable. That's probably why windows stopped booting from it.

---

