---
title: "Knoppix Newbie - Help Recovering Files from 8TB External Raid Drive"
date: 2016-05-21
forum: Ubuntu/Debian BASED
---

### Post by anthony99 on 2016-05-21
Good day to all!

First of all, i'm a newbie to all Ubuntu / Linux / Knoppix system. I just started experiencing the Linux interface like 12 hours ago. So I wanna thank you in advance for any help you may give me.

My issue goes like this:

I have a Raid 0 enclosure (2x Seagate 4TB = 8TB Total in an enclosure with a brand name of Marshal which I bought from Japan last year).
The 8TB was originally plugged-in my Asus laptop running Windows 7 - 64Bit.
Sudden power surge, and my laptop made a windows unplugged USB sound.
Check 'My Computer' and my 8TB was not there.
I plugged-out the USB (of my 8TB), and plugged it in again. Windows still gave it's usual sounds. But still no Autoplay.
Repeated this a few times, and my Windows did the same.
Finally decided to launch 'Disk Management', and there it was. My 8TB shown, but under 'Unallocated Space', and an error popped-up saying that my 8TB needs to be 'Initialized'.
I cancelled that error as we all know what that means.
I tried scanning (not writing or recovering, just scanning) my 8TB using GetDataBack and R-Studio, and found that my files are still there.
Googled for a whole day, and with an advise from a friend, led me to Knoppix.
I was advised that I could try accessing my 8TB using Linux / Knoppix.
I'm now running Knoppix 7.6 using my desktop, but I'm stuck with Mounting my 8TB.
Under 'File Manager PCManFM', my 8TB shows as 'sdc'.
From this forum, I've managed to learn a few LXTerminal commands like '*showmount*', '*sudo*', '*mdadm*', and the likes.
But one must admit when one has finally hit a wall.
I am getting errors like '*wrong fs type bad option bad superblock*', '*mdadm: must be a super-user to perform this action*', and '*does not appear to be an md device*'.
I'm just hopeful that I can recover my 7TB worth of data.
Hope you guys can help.
Thanks again in advance.

PS: Should I be on a wrong forum, please accept my apologies. I'm also a newbie with forums, but I can't think of a better solution but from experts like you. Thanks again.

- Tony

---

### Post by deadflowr on 2016-05-21
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by oldfred on 2016-05-22
Do not know about Knoppix and what versions they use. And do not know RAID but can give you some links that may have examples.

Older link more on install:
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.  So older instructions may refer to dmraid but use mdadm.
And then drives should be seen as /dev/mapper/xxxxxxxx.

RAID 0 was used by those who needed speed at all cost. Perhaps gamers or those who compiled systems for a living. But not for data. And if USB external drive, most of you speed of drives was lost in USB port speed.


 Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

If an NTFS partition and you see your data, best to recover that right away. 
We normally suggest Windows tools for Windows and Linux tools for Linux. But sometimes when Windows tools do not work, Linux may be able to help.
But for data recovery the NTFS tools in Windows usually work well.

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

---

### Post by anthony99 on 2016-05-22
Thank you oldfred!

Will check out the links you suggested. 

I'm planning to install an Ubuntu system in my desktop, I think that would be better.

My question now is, would Ubuntu really be able to read my 8TB? And I can recover my data? I'm sure that I'm using the wrong commands in Knoppix which is why I'm unable to mount it properly. 

I'm still hesitant in using Recovery software in Windows as it will re-write the whole array causing me to recover only partial data.

Hope you can atill help me out when I finish installing Ubuntu. 

Thanks so much again and have a nice day. 

- Tony

---

### Post by anthony99 on 2016-05-22
Hello again!

I finally installed Ubuntu 16.04.

I plugged in my 8TB External Raid drive, but it did not appear on the File Manager.

I opened Terminal, typed:* sudo lshw -C disk*
It asked for a password, and I typed it in.
This was the response:

*-disk
        description: SCSI Disk
        physical id: 0.0.0
        bus info: scsi@25:0.0.0
        logical name: /dev/sdb
        size: 7452GiB (8001GB)
        confguration: logicalsectorsize=4096 sectorsize=4096

Also, I checked Disk Utility and the 8TB is visible there.

Any suggestions how to proceed?

Thanks again in advance.

- Tony

---

### Post by oldfred on 2016-05-22
Standard install would not give you the RAID drivers.
You need to install mdadm
 sudo apt-get install mdadm 

Not sure if it will directly see the RAID partitions or not, have not used RAID of any type and there are many types.

But you cannot recover to the same drive you have data on. You need up to another 8TB to copy data to from recovery software whether Windows or Linux.
If data was/is valuable, you should have that anyway or some way to copy data to other device(s).

Also if NTFS, the Linux NTFS driver will not normally mount NTFS partitions that are hibernated (most Windows 8 are hibernated as fast start up is hibernation) nor will mount NTFS that needs chkdsk. And those issues can only be fixed from Windows.
You may be able to mount read only (ro).
I have an example, but not RAID, your  device should be something like /dev/mapper/xxxxxxx where xxxxx is your specific RAID.


        sudo mkdir /media/windows
sudo mount ntfs-3g -o ro /dev/<device-name> /media/windows

---

### Post by anthony99 on 2016-05-22
Thank you again oldfred! I'm sure glad you're still there.

I tried the command:
*sudo apt-get install mdadm *

But I got this response:
[I][sudo] password for anthony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mdadm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'mdadm' has no installation candidate[/I]

I believe I have 2 more sets of bland 4TB for the copying of my files (that i'm recovering from the 8TB). 

The OS from which my 8TB came from is running Windows 7 (64 bit). But I'm sure it's NTFS.

When you say "read-only", does this mean that I can still copy the file/s and back them up on my new HDD's? My only goal is to have the 8TB access via Ubuntu so that I can back-up my files to my new set of HDD's.

Thanks again oldfred! Much obliged!

PS: So sorry for this, but I don't know what to do with your last command code/s:
[I]sudo mkdir /media/windows
sudo mount ntfs-3g -o ro /dev/<device-name> /media/windows[/I]
Sorry. But should I execute these after installing mdadm, or should we first settle the issue with the installation? Thanks again.

---

### Post by oldfred on 2016-05-22
You have to get mdadm installed first.
Do you have repositories configured? Check System Settings, Software & Updates icon. I have main, universe, restricted & multiverse checked. But that was default with my install?
I just installed to a flash drive and part of uninstall at end of install process it removed mdadm, plus many other packages in installer.

My results:
fred@Z170N:~$ sudo apt-get install mdadm 
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  default-mta | mail-transport-agent
The following NEW packages will be installed:
  mdadm
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 394 kB of archives.
After this operation, 1,200 kB of additional disk space will be used.

Lot of install steps.
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.

And of course I have no array to find.


You have to mount after you install mdadm, otherwise you cannot see the RAID drive.

---

### Post by anthony99 on 2016-05-23
Good day oldfred!

I finally updated my Ubuntu. I executed the mdadm command and surely everything you said appeared. I've also check System Settings and have main, universe, restricted & multiverse checked. Blow is the complete commands and replies from Terminal:
```
[I]anthony@IronMan:~$ sudo apt-get install mdadm
[sudo] password for anthony: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
anthony@IronMan:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
anthony@IronMan:~$ sudo apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  default-mta | mail-transport-agent
The following NEW packages will be installed:
  mdadm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 394 kB of archives.
After this operation, 1,200 kB of additional disk space will be used.
Get:1 [http://ph.archive.ubuntu.com/ubuntu](http://ph.archive.ubuntu.com/ubuntu) xenial/main amd64 mdadm amd64 3.3-2ubuntu7 [394 kB]
Fetched 394 kB in 3s (125 kB/s) 
Preconfiguring packages ...
Selecting previously unselected package mdadm.
(Reading database ... 204402 files and directories currently installed.)
Preparing to unpack .../mdadm_3.3-2ubuntu7_amd64.deb ...
Unpacking mdadm (3.3-2ubuntu7) ...
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for doc-base (0.10.7) ...
Processing 4 added doc-base files...
Processing triggers for man-db (2.7.5-1) ...
Setting up mdadm (3.3-2ubuntu7) ...
Generating mdadm.conf... done.
update-initramfs: deferring update (trigger activated)
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-4.4.0-21-generic
Found initrd image: /boot/initrd.img-4.4.0-21-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Processing triggers for systemd (229-4ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for initramfs-tools (0.122ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.[/I]
```

Please advise how to proceed with mounting command.

Thanks again. You're replies are very much appreciated.

-Tony

---

### Post by oldfred on 2016-05-23
Please use code tags on longer text or terminal output.
Easy to add with forum's advanced editor and # icon.

I do not know RAID, but this may show commands you need. 
You may just want manual assemble?
[http://askubuntu.com/questions/581473/fakeraid-in-ubuntu-14-04-wont-auto-assemble-on-boot](http://askubuntu.com/questions/581473/fakeraid-in-ubuntu-14-04-wont-auto-assemble-on-boot)

---

