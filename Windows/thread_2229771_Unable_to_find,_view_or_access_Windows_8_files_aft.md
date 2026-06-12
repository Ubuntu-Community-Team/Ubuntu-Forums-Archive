---
title: "Unable to find, view or access Windows 8 files after Ubuntu install"
date: 2014-06-15
forum: Windows
---

### Post by xdonbaldwin on 2014-06-15
Hi I have a really screwed up situation that I'm hoping someone on here will be able to help with.  Back story: I went on a trip to visit relatives and left my laptop at home thinking that was the best place for it (I was apparently wrong).  I had given a friend of mine a key so that he could feed, give water, and let my dog out while I was gone.  When I returned I found he had taken very good care of my dog but my laptop which originally had Windows 8 on it now had Ubuntu on it. 
 
          It gives me a Windows 8 option on the start up screen but when I hit it I'm told I need a Windows 8 disk to restore to Windows.  This really worries me because I had A LOT of Photos, Music, and Movies on my laptop that I can't replace (I know I should have done a full backup before leaving but I was retarded and didn't).  When I asked him about it he said that everything was still on there and that I only needed to get a Windows 8 disk and I would get it all back. 

          I'm worried he either doesn't know what hes talking about or lied because I can't find any sign of them through Ubuntu and haven't been able to get a Windows 8 disk to test it.  What I'm wanting to know is if there is anyway to definitively find out whether the files are still there without using a Windows 8 disk?  If they are still there is there anyway I can access them now or do I need to wait for the disk to retrieve them?  I know this all probably sounds really dumb but I have been trying to find answers to these questions for a while now and can't seem to find anyone with the same problem.  I'm really hoping someone on here can answer my questions and hopefully help me get all this mess sorted out. 

 Thank you for your time and energy in trying to help me.

---

### Post by Bucky Ball on 2014-06-15
You will not get far with a 'black blob' of text. Please provide paragraphs. Many, including me, will take one look at the above and move on. Hurts my eyes! Thanks.

---

### Post by The Cog on 2014-06-15
If you're still on speaking terms with this "friend", it would be easiest to get him to copy all your files onto an external drive. 
If not, can you get into Ubuntu yourself? The file manager (should not be too hard to find) will be able to show you all the drives on the machine (sometimes pressing F9 makes a side-panel appear/disappear which can list the devices). An external drive should also appear in that list when you plug it in, so with two file manager windows, you can drag/drop between the two.

Failing that, can you tel us how far you get so we can give instructions from there.

Ultimately you may well need a windows disk to either repair or reinstall.

---

### Post by xdonbaldwin on 2014-06-15
Thank you both for your replies.  I took your advice Bucky Ball and edited the post let me know if it needs anymore editing.  He isn't returning my calls which is another reason I started thinking he had lied about the files still being there.  I'm currently using Ubuntu seeing how its the only option I have right now and the file manager shows multiple devices off to the side and I have no external devices attached at the moment.

19GB Volume
XP
9.1 GB Volume
7.5 GB Volume
27 GB Volume
54 GB Volume
Computer

I'm not sure which one would hold the Windows 8 files, but when I use the magnifying glass icon at the top and search all files for a folder I had on Windows 8 it comes back with nothing.  I don't know exactly what I'm supposed to search for in order to find out.

---

### Post by oldfred on 2014-06-15
Many users forget to turn off the fast boot or always on hibernation and then Linux NTFS driver will not mount the hibernated system. 
You have to boot into Windows and turn it off. If a new UEFI system, you may be able to directly boot from UEFI menu or one time boot key into Windows if your "friend" did not erase it.

Best to see details. Boot-Repair only fixes a few minor Windows issues. For Windows you do need a Windows repair flash drive.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by yancek on 2014-06-15
The first thing you could do is open a terminal from Ubuntu, type the following command:  sudo fdisk -l(Lower Case Letter L in the command)  You will be prompted for the primary user password.  I hope your 'friend' gave you that?  This command will output information on drives/partitions.  Sample entry below.  The first column is Device and below shows /dev/sdb1.  That would be the first partition on the second disk.  Make a note of what you see only for the partitions which have "HPFS/NTFS/exFAT" under the System column as shown below.  You should then be able to mount the partition and look to see if your files are there.  If you dont see any ntfs partitions, bad news.
 
```
/dev/sdb1   *        2048     7903979     3950966    7  HPFS/NTFS/exFAT

```

You can mount with the command below, changing the sdb1 to whatever is correct on your system.  If it fails, post the output.  Before running the command below, create a mount point with:  sudo mkdir /mnt/windows

> sudo mount -t ntfs-3g /dev/sdb1 /mnt/windows

---

### Post by xdonbaldwin on 2014-06-15
When I enter the command: sudo fdisk -l and enter my password this is what it tells me

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1efad293


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

:-(  I'm guessing that's bad.

---

### Post by oldfred on 2014-06-15
No, it just is you have a newer UEFI system that has to have gpt partitioning. The fdisk command only works on older BIOS boot system with MBR(msdos) partitioning.

You can run this command to see partitions, Boot-REpairs BootInfo report does that plus many other commands automatically and copies report to paste bin so we can see it.

sudo parted -l

---

### Post by xdonbaldwin on 2014-06-15
Ok I followed the instructions in the link to get boot-repair and ran Bootinfo shown in the link below, while running Bootinfo the files and folders on my desktop disappeared is that normal and did they just get moved somewhere? 

[http://paste.ubuntu.com/7648533/](http://paste.ubuntu.com/7648533/)

---

### Post by Bucky Ball on 2014-06-15
There are major issues with your Ubuntu install. It may well have something to do with UEFI. oldfred may be able to help you out. Note well what he has to say on the subject, but it looks grim. Something has gone wrong. Windows and your NTFS partitions look intact, though. It's just the Ubuntu install that appears to have gone pear-shaped.

---

### Post by xdonbaldwin on 2014-06-15
Well that's both good news and bad news at the same time.  Thanks Bucky Ball for advising me on my original post mistake and for taking the time to look over my info.  If I had kept making that mistake my questions might have never gotten answered lol.  If things keep progressing like they are I'm sure this problem will be fixed in no-time.  It's great that Windows could be intact because I don't have anyway of re-installing that right now, Ubuntu on the other hand seems to have a ton of ways of to either repair or replace.  :-)

---

### Post by xdonbaldwin on 2014-06-15
Oldfred should I try to mount sda1 now using the command line yancek told me?

[COLOR=#000000]*[ sudo mount -t ntfs-3g /dev/sdb1 /mnt/windows ]*[/COLOR]

---

### Post by oldfred on 2014-06-15
Your buddy really messed with your system and did not know what to do on a new UEFI type system.

There is a wubi install in your Windows NTFS partition  sda3. Wubi does not work with gpt partitioned drives which UEFI requires. Hopefully we can get back to Windows but may need several repairs. 
Do have have access to another Windows 8 system at work, school or friend? You will need a Windows repair flash drive to get Windows working.
You also seem to have another Windows 8 in sda6. Did he copy it as a backup?

It looks like multiple installs were tried, you show 13.10 in sda10 and 14.04 in sda18.
You seem to have several bios_grub partitions which are required with a BIOS boot on a gpt drive. You show 3 swap partitions, so it looks like three installs (plus wubi) were tried.

With UEFI/gpt the boot flag determined which partition is the efi partition. That partition has a folder for every system installed and efi files for UEFI to find and use to boot.
In BIOS the boot flag is only used by Windows and has to be on the primary partition (MBR only) with the Windows boot files. Either a small boot partition or the main install.
You now have the boot flag on the main Windows install so UEFI thinks that is an efi boot partition but it has no efi folders. Your buddy moved boot flag to main Windows install like you would with BIOS, but that breaks UEFI boot.

The efi partition also must be FAT32 formatted and the Windows default is usually about 100MB near the beginning of the drive. And that partition is not shown. You do show a FAT32 partition sda4, normally the efi partition is before the Windows main install. And the sda2 looks like the required system reserved partition that must be before the Windows partition, usually just before it. But it should be after the efi partition.

 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

So I do not know if partitions were copied and moved around or not. I also have seen where script misses showing files if partition structure is not correct. Do you have in your sda4 a Microsoft folder with efi files plus others?

It looks like if you let Boot-Repair reinstall grub of the 14.04 install in sda18 into the MBR that then you could boot that if in your UEFI menu you have UEFI boot turned off and BIOS/CSM/Legacy boot turned on.

It does show you booted live installer in BIOS mode. It should actually show two modes one UEFI and one not UEFI or usually just the name/label of the flash drive.
Boot repair can convert a BIOS install to UEFI, but we have to resolve multiple issues first.

Script is not saying it cannot mount any of your NTFS partitions, so they may not be hibernated. Can you mount either or both sda3 & sda6 and see your files? That would be great if you can. And immediately backup everything to another device, flash drive or hard drive.

---

### Post by xdonbaldwin on 2014-06-15
Alright just to make sure I don't screw anything up, I need to use this first -

[COLOR=#000000]sudo mkdir /mnt/windows  [/COLOR]

Afterwards do I enter the command like this -

[COLOR=#000000][I]sudo mount -t ntfs-3g /dev/sdb3 /mnt/windows

Or do I need to actually enter windows 8 in place of windows?[/I][/COLOR]

---

### Post by oldfred on 2014-06-15
You posted while I was composing the long post above.
You can try mounting both sda3 & sda6 as you do not have a sdb except the live installer. A few systems do promote a flash drive to sda and make hard drive sdb, so always good idea to check with parted or other tools to be sure which drive is which.
If they mount ok, you should just be able to use Nautilus file browser to click on the partitions, or use Disks, or gparted to mount. if gparted shows red or yellow warning triangles right click on those but will will give standard error where it typically is hibernated and will not mount.
If manually mounting you have to use different mounts for each.

---

### Post by xdonbaldwin on 2014-06-15
Ok so I understood some of that lol Let me see if I'm even close.  What your saying is I need to use a program called parted to check and see which driver is which.  Then I have to install the Disks or gparted program and use that to try and mount both of those partitions.  If I use the terminal then I have to use different mounting locations to mount them too?

---

### Post by sudodus on 2014-06-15
***parted and gparted*** come with all Ubuntu flavour install iso files, so you have them already. ***Disks*** come with some on the iso files.

You can mount the partitions one after another, but you can also mount them at the same time (but of course to different mount points).

For example: devices 'sda3 & sda6'

1. create mount points

```
sudo mkdir /mnt/sda3
sudo mkdir /mnt/sda6

```
2. mount each device

```
sudo mount /dev/sda3 /mnt/sda3
sudo mount /dev/sda6 /mnt/sda6

```
If the mounting is successful, you can browse to the mount point with a file browser or use terminal window commands. Remember that you should go to the mount points

**/mnt/sda3** and **/mnt/sda6**

in order to see directories and files. So this is a critical step and depends on the way Windows was shut down (hibernated or a complete shutdown).

(If this is successful, you should also be able to copy files to another drive, where you have also mounted a partition, and where you have write access. You might need to copy with superuser privileges in order to perform the copying. But that is the next step.)

-o-

Edit: You can run the command

```
df
``` and post the output after trying to mount the devices

---

### Post by xdonbaldwin on 2014-06-15
Ok so this is what I get after I ran the mounting codes

 
```
df: ‘/root/.gvfs’: Permission denied
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda18      12670272  11094816    908784  93% /
none                   4         0         4   0% /sys/fs/cgroup
udev             2822696        12   2822684   1% /dev
tmpfs             566452      1376    565076   1% /run
none                5120         0      5120   0% /run/lock
none             2832240     45400   2786840   2% /run/shm
none              102400        68    102332   1% /run/user
/dev/sda10      51481784   5129616  43713988  11% /media/goomba/a076baac-66a4-4382-bedc-74b7ccaa8207
/dev/sda3      309061356 284321764  24739592  92% /mnt/sda3
/dev/sda6        9585660    943420   8642240  10% /mnt/sda6
```

Apparently I have to have root permissions to access the folder they are mounted in?

---

### Post by sudodus on 2014-06-15
> **xdonbaldwin said:**
> Ok so this is what I get after I ran the mounting codes

 
```
df: ‘/root/.gvfs’: Permission denied
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda18      12670272  11094816    908784  93% /
none                   4         0         4   0% /sys/fs/cgroup
udev             2822696        12   2822684   1% /dev
tmpfs             566452      1376    565076   1% /run
none                5120         0      5120   0% /run/lock
none             2832240     45400   2786840   2% /run/shm
none              102400        68    102332   1% /run/user
/dev/sda10      51481784   5129616  43713988  11% /media/goomba/a076baac-66a4-4382-bedc-74b7ccaa8207
[COLOR=#ff0000]/dev/sda3      309061356 284321764  24739592  92% /mnt/sda3
/dev/sda6        9585660    943420   8642240  10% /mnt/sda6
```[/COLOR]

Apparently I have to have root permissions to access the folder they are mounted in?

I added code tags to make the output easier to read.

The [COLOR=#ff0000]red lines[/COLOR] show that you can mount and read the partitions. So please use the file browser and browse to **/mnt/sda3** and further down in the file system. I think you can find and read files there. And the browse to **/mnt/sda6** ... :-)

---

### Post by xdonbaldwin on 2014-06-15
Oh yeah sda3 has all the files I was trying to save on it and I'm not sure what sda6 is from.  It looks like just a generic Windows 8 OS. Thank you guys sooo much for helping me access all those files, you have no Idea how much this means to me.  So I'm guessing the next step is find something to back-up all these files on and then either find a way to do a Windows 8 restore without a restore disk or a Windows 8 disk or wait to finish fixing it until I have a disk.

---

### Post by sudodus on 2014-06-15
Congratulations to having found the files you need :KS

I think the next step is rather straightforward. Get a big external drive to back-up all these files.

After that I think you should ask for *oldfred*'s advice. He might be able to help you repair Windows without re-installing, now that we know that the file system is good.

---

### Post by oldfred on 2014-06-15
Backup, of course is first priority.

But you probably will have to have if Windows repair flash drive as all the size changes mean it needs chkdsk and chkdsk is one thing that cannot be done from Linux. But you may be able to get into Windows own repair tools with f8 if we can get it booting or perhaps set the chkdsk flag from ntfsfix so it does run it on a reboot. But not sure if booting will work.

Did you look in the FAT32 partition to see if it has any .efi files? There usually are backups in Windows also.
But we will need a valid FAT32 partition with the boot flag to make it the efi partition and have Windows boot files in that partition. And then boot in UEFI mode not BIOS mode.

You should have a folder like this:
 /EFI/Microsoft
And I think these are the very minimum needed to boot with in UEFI boot mode.
      
 /EFI/Microsoft/Boot/bootmgfw.efi
     /EFI/Microsoft/Boot/BCD



 If .efi files do not exist we should be able to copy the minimum files need to boot from Windows, but may need a third party Windows repair tool to fix /boot/BCD if that is not in current FAT32 partition.

---

### Post by xdonbaldwin on 2014-06-15
Yeah a USB drive or a CD absolutly WILL NOT hold it all.  I have over 2,000 songs, 66 pictures, 60+ full length HD/BlueRay movies, and a few games on here lol.  With my laptop being screwed up system information says that the Laptops full Disk space is 13GB and the Memory is 5.4GiB.  

What it really has (that I can't use while it is screwed up) is :
Disk - 500GB SATA
Memory - 6GB

That probably explains when even though it was saying Disk space was 13 GB there are Volumes on the side of the File Explorer that are 54GB, 27GB, 19GB, 9.1GB, and 7.5GB.  Even with the Computer Volume that is right below them that is only 128.1GB that Ubuntu was accessing lol.

Thank you guys again for all the help and I am eager to find something to hold all these files so I can continue with the repair process.

---

### Post by oldfred on 2014-06-15
Your Windows was shrunk a lot and many small partitions created. 

You need the Windows default UEFI partitions. Not sure if recovery partitions still exist. There are usually two recovery partitions. One is just the Windows repair partition which for some reason it calls recovery and the vendor image of the hard drive which is the vendor recovery. That is now the standard instead of shipping recovery Windows installer. You are supposed to immediately make a recovery DVD set in case hard drive fails, but in most cases you can just use it to restore system to like new. Many totally erase drive, but some will save you data. Always best to have a full image backup and a repair flash drive.

Do you want Ubuntu also or just repair Windows? If just Windows I will move thread to OtherOS and suggest also looking at the windowseight forum. I do not really know Windows other than what others have suggested.
       [http://www.eightforums.com/](http://www.eightforums.com/)

At the very least we need to restore an efi boot partition with Windows boot files. Have you looked in your FAT32 partition to see what is in it?

---

### Post by xdonbaldwin on 2014-06-15
Ill probably start with just getting Windows 8 back up and running and then after that is done I was thinking about adding a bootloader (probably Grub) and then installing OpenSUSE 13.1 but still need to check to see it is compatibility with my laptop, wifi card, graphic card, and sound card.

---

### Post by Bucky Ball on 2014-06-15
Grub generally installed during OS install. Please post any support requests for Opensuse, if you have them, in the ***Other OS/Distro Support*** forum, or better still, on the Opensuse forums. Good luck.

---

### Post by oldfred on 2014-06-15
Moved to OtherOS since really just Windows.

After you have the backups done, come back and we will re-review partitions. Many can be deleted, but you need to reconfigure or add some essential ones.

---

### Post by xdonbaldwin on 2014-06-16
Ok so I have been working hard all day trying to get everything worked out and I have made some progress.  After literally 4 hours I managed to back up all the files I absolutely don't wanna lose.  Now I'm back to not being able to figure out how to create a USB boot drive.  I know the info is probably all over the place, but I can't seem to find it and don't even know what all that entails.  I feel like I'm soo close and yet can't seem to reach it.  Please someone help me reach a conclusion on this problem.

Thank's again for your time.

---

### Post by yancek on 2014-06-16
What do you want to make a bootable usb drive of, windows 8?  Probably have better luck at the support.microsoft site or some windows 8 forum.  If you are trying to get windows 8 running again, you might be able to use a friends install medium which should have a repair option.  It would probably have to be the same version you were using.

---

### Post by xdonbaldwin on 2014-06-16
Alright Ill give that a shot seeing and thank you for the speedy response.

---

### Post by oldfred on 2014-06-16
In post #5 I have links to details of a Windows 8 repair flash drive. That has to be made from a working Windows 8. Best to do when system is working, but if you have access to another Windows 8 system you can use that if same version.

If making a new Ubuntu live installer:
 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by xdonbaldwin on 2014-06-16
Seeing how I already retrieved the files I wanted to keep and have already backed them up I'm ok with reformatting the hard-drive and re-installing Windows 8.  I actually need access to Windows 8 right now because my mind is getting fried after all the work to fix this thing and I need a short break from command lines lol.

---

### Post by oldfred on 2014-06-16
If it is Windows 8, your product key is in UEFI and only works with your vendor's specific version. Or the version from the recovery partition or the backup of that partition that you make as soon as you get new computer as vendors stopped providing DVDs.

If you do not have the vendor version you may be able to get one for a nominal charge from the vendor (do not mention Linux was issue). Or else you have to purchase a full new copy of Windows.

---

### Post by xdonbaldwin on 2014-06-19
Ok so forgot all about this thread and opened another one, If the new one isn't needed then it can be deleted but the question on there is still what I'm trying to figure out.  I haven't been able to get any way to reformat the computer (because I don't have the product key and I don't have a USB device to make a live CD or anything) and I can't find a good way to fix this problem.  I'm sorry I have been extremely difficult and I am probably getting really annoying but this problem keeps throwing me curve balls.  I tried taking a break from it to try and gain perspective of the situation but that hasn't helped and has actually caused me to forget where I was at solving the problem.

---

### Post by Bucky Ball on 2014-06-19
The other thread is closed with a link to this one.

---

### Post by xdonbaldwin on 2014-06-20
Thank you soo much Bucky my brain is kinda fried after all the work trying to get it fixed.

---

### Post by oldfred on 2014-06-20
Did you make a Windows 8 repair flash drive as per post #8. Anyone with a 64 bit or UEFI version of Windows 8 can make it for you.

Did you order a recovery set of DVDs from Vendor?

Did you reread post #13.
And do you have .efi files in sda1. It is now shown as a NTFS formatted partition but often the first or second partition is a FAT32 efi boot partition. You will have to have an efi partition to boot/repair Windows and if sda1 was just changed it may still have boot files? Or what is in sda1?

Did you fix Ubuntu just to have a working system, or reinstall it? 
It looks like lots of extra partitions could be deleted to clean it up, but you have to be careful not to delete ones you really need. We can only really help on Ubuntu install issues and only know a little about Windows issues from those that have dual booted an showed us issues & how to resolve them.

---

### Post by xdonbaldwin on 2014-06-20
I don't know anyone else with Windows 8 so could have anyone help me with the Windows 8 repair flash drive.

I am trying to get a hold of the Microsoft support desk to figure out what the what I need to do to get a recovery set.

I'm trying to get both working because I need Windows for some of my work programs (I'm going to be starting a new job soon and they ask that I have Windows).

I was going to delete some of the extra partitions but don't know which ones I can delete and don't know what all I can do to try and clean it up a little.

I understand you guys a mainly for Ubuntu and truly appreciate all the help I have gotten thus far.  I'm not trying to be pushy or anything of the sort.  I'm just really frustrated because I need this job and my laptop is being really difficult.  That is why I was going to just reformat the hard drive and start fresh, I thought that was going to be the fastest fix but I am finding that is not the case.

---

### Post by oldfred on 2014-06-20
What is in sda1? Anything?
We need a efi partition which is FAT32. If sda1 has them we will convert back to FAT32 (not reformat, just change type). If no data at all we can reformat and move boot flag to sda1. But let me know what is in it first. Then I can post some steps that may get you booting, no promises.

Microsoft will tell you to contact your hardware vendor, they do not support the versions included with a computer, your vendor does. 

What brand/model is it?

UEFI installs of Windows have  a backup of bootmgr and you can use third party tools to recreate a BCD which are the two main files you need to boot.

---

### Post by xdonbaldwin on 2014-06-20
Ok so sda1 has 
[U]
File system[/U][COLOR=#000000]:       ntfs 
[/COLOR][COLOR=#000000]Boot sector [/COLOR][COLOR=#AA22FF]type[/COLOR][COLOR=#000000]: [/COLOR]_Windows_[COLOR=#000000] 8/2012: NTFS
[/COLOR][COLOR=#000000]Boot sector info:  No errors found in the Boot Parameter [/COLOR]_Block_[COLOR=#000000].
[/COLOR]_Operating System_[COLOR=#000000]:  
[/COLOR][COLOR=#000000]Boot files: 
       [/COLOR]
and it shows FAT32 in sda4 which shows a boot sector type: Windows XP

I have an HP Pavilion g7-2269wm laptop PC

Where would I look to find the backup bootmgr?

---

### Post by oldfred on 2014-06-20
If you mount sda1 and sda4

Manual mount, must be unmounted if mounted automatically by nautilus file brower. Do this for both sda1 and sda3
       sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1

cd /mnt/sda1
ls -l
If you see a Microsoft folder or an efi folder change to it. I want to see if any efi files.
cd /Microsoft
ls -l

This issue is the efi partition should be first, but it is bit unusual to have a FAT32 later on drive with UEFI system. Maybe the original efi partition was copied like the main c: drive? And then sda1 reformatted. If sda1 is empty I would prefer to convert it to the efi partition. And if either have a Microsoft folder with efi files that would be great.

---

