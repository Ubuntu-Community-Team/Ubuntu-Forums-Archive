---
title: "easy2boot - How to easily boot multiple ISOs from a single USB drive"
date: 2013-10-14
forum: Tutorials
---

### Post by allcoms on 2013-10-14
I have already posted this exact tutorial on linuxmusicians.com but I realise its useful to ALL x86/x64 users, Linux-using musician or not. I thought I'd reproduce it here to get it the attention I feel this info deserves.

unetbootin only allows you to boot one ISO per USB drive - easy2boot lets you boot as many ISOs as you can store on your drive and adding new ISOs is as simple as copying them into the correct folder so its platform neutral in that respect, not requiring you to run an updater as you do with say YUMI, which is Windows only. I have tried other Linux-friendly apps (multisystem etc) that have claimed to do this but none of them worked properly. Every ISO I have tested with E2B has worked 100% and I have tried at least a dozen distros, diagnostic and recovery ISOs with it now.

Here's a quickstart guide to setting up easy2boot on your USB drive, based upon instructions from [http://en.positon.org/tag/Easy2Boot](http://en.positon.org/tag/Easy2Boot) 

Your easy2boot drive can be formatted as FAT32, NTFS or ext2. FAT32 is compatible with more computers and operating systems but has a 4GB max file size limit, which is too small for some DVD images although very few Linux distributions exceed 4GB. If you use ext2, you will not be able to install Windows OS's from your e2b drive. NTFS does not have a 4GB file size limit like FAT32 but you can't read/write NTFS on as wide array of platforms as FAT and in addition I've experienced difficulties booting ISOs from an NTFS formatted drive that was created under Linux due to non-contigious files that can't be defragged under Linux. Hence, FAT32/vfat is the recommended filesystem for e2b drives. You can use gparted to graphically format drives or you can use a command like:

```
sudo mkfs.vfat -n easy2boot -F 32 /dev/sdx1
```

to format a drive as FAT32. Replace sdx1 with the device to be formatted.

Download Easy2Boot ( [http://www.easy2boot.com/download/](http://www.easy2boot.com/download/) ) and extract all the files in the zip to the root directory of your e2b drive.

Download grub4dos ( [https://code.google.com/p/grub4dos-chenall/downloads/list](https://code.google.com/p/grub4dos-chenall/downloads/list) ) and extract the archive on your PC (not on the usb stick). Its author seems to release a stable and a testing version but I'm unclear on their versioning and release scheme at present. For its current batch of releases, grub4dos-0.4.5c-2013-07-24.7z works fine with my Samsung R700 but grub4dos-0.4.6a-2013-07-24.7z does not so try an older or newer G4D version if you get an error like 'This is not a bootable device' when you try booting off a E2B/G4D enabled drive.

To install grub4dos on your USB drive, run this from within the grub4dos dir:

```
sudo ./bootlace.com --time-out=0 /dev/sdx
```
to install grub4dos to the MBR of the specified device but make sure you use the right device! `df` and `fdisk -l` are your friends here.

Finally, copy some ISOs to the _ISO/MAINMENU directory then reboot! Make sure your machine is set to boot off USB storage first - many devices let you enter the boot menu by pushing F11 or F12 when they are booting BIOS/UEFI.



NB easy2boot requires the iso's be stored as contiguous files on your USB drive. When you start deleting iso's then copying new ones on, the files can become fragmented sometimes and refuse to boot. I found this tool to defrag drives under Linux. Maybe there's a better one? Its a perl script that must be run as root but seems to do the trick:

[http://defragfs.sourceforge.net/](http://defragfs.sourceforge.net/)

After downloading and un-gzipping the defragfs script, you'd run it with a command something like this:

```
sudo perl defragfs.pl /media/dan/easy2boot/ -f
```

You need to change /media/dan/easy2boot to the path of the drive you want to defrag and defrag.pl to the name of the defragfs script.

Apparently defragfs is only intended for use with ext filesystems but in my experience it also works fine for FAT32/vfat drives. It does not work wth NTFS partitions.

---

### Post by SuperFreak on 2013-11-07
I also discovered Easy2Boot recently and am quite pleased with it. So far though I have only been able to get noncontiguous files sorted by putting my USB in my Win 7 machine and running RMPrepUSB. I tried your instructions dropping the extracted defragfs file in my home directory. Issuing the command you wrote "sudo perl defragfs.pl " resulted in not found in terminal

---

### Post by sammiev on 2013-11-07
I will follow this thread and try it when I get a few hours to play. :)

---

### Post by SuperFreak on 2013-11-07
Thanks sammiev

If I try the code on a folder in my Home dir this is what I get

```
david@MainSqueeze:~$ sudo perl defragfs.pl /home/david/Dropbox/ -f
[sudo] password for david: 
Can't open perl script "defragfs.pl": No such file or directory
david@MainSqueeze:~$ 


```

Drop box was just a test folder

---

### Post by SuperFreak on 2013-11-08
I didn't realize that it was necessary to append the defragfs with .pl to make this work . Once I changed the file defragfs to defragfs.pl defragging worked. Down to my inexperience with commands I guess


Edit: Emailed the author of defragfs, J.Robson. It is only intended for Linux file systems (EXT2,3,4) not FAT32 or NTFS. This explains why it works on my PC files which are EXT4 but not the USB key which is FAT32

---

### Post by sammiev on 2013-11-08
Good to know before I jump in. thanks

---

### Post by allcoms on 2014-04-10
Updated guide to fix e2b download link to point to its new web site,  removed NTFS formatting command (FAT32 is recommended for Linux users at  least) and added notes on defragfs vs FAT32 and NTFS.

Superfreak:

Contrary to what the defragfs author says, I know through having successfully used defragfs on FAT32 drives many times that it does work on such drives. However, It DOES NOT work with NTFS. I've had no real success with e2b and NTFS drives created under Linux. You get to the menu but ISOs don't boot as they're non-contigious.

I also highlighted that 'defragfs.pl' needs to be changed to the name of your defragfs script.

---

### Post by SuperFreak on 2014-04-12
Thanks for the updated guide([GUIDE]("http://linuxmusicians.com/viewtopic.php?f=19&t=11479")). I will try rebuilding my E2B USB and use FAT32 format. I had some misconception that I might be using files bigger thasn 4 GB which wouldn't work on FAT32.

---

### Post by sammiev on 2014-04-13
I read up on the new links and tried it and a few older versions with no luck. I just get a Grub Rescue prompt on boot. It sounds and reads so simple but just no joy. Even tried a few different USBs.

---

### Post by SuperFreak on 2014-04-13
repeat post

---

### Post by SuperFreak on 2014-04-13
> **sammiev said:**
> I read up on the new links and tried it and a few older versions with no luck. I just get a Grub Rescue prompt on boot. It sounds and reads so simple but just no joy. Even tried a few different USBs.

Not sure if this is the issue but I couldn't get it to work when I changed directory in terminal to  grub4dos and issuing this command
-```
sudo ./bootlace.com --time-out=0 /dev/sdx
```
as per directions. However when I Changed directory to the folder where bootlace.com was located(one level down) in the  grub4dos directory it did work
Hope that helps


Also when using the defrags script I removed the .pl suffix on the file name and used the specific file name as directed

---

### Post by SuperFreak on 2014-04-13
sorry  for multiple posts only the last one was needed

---

### Post by sammiev on 2014-04-13
> **SuperFreak said:**
> Not sure if this is the issue but I couldn't get it to work when I changed directory in terminal to Easy2Boot USB and issuing this command
-```
sudo ./bootlace.com --time-out=0 /dev/sdx
```
as per directions. However when I Changed directory to the folder where bootlace.com was located(one level down) in the Easy2Boot USB directory it did work
Hope that helps


Also when using the defrags script I removed the .pl suffix on the file name and used the specific file name as directed

I will give it another try. Thanks

---

### Post by sammiev on 2014-04-13
My bad.

I was using /dev/sdb1 instead of /dev/sdb.

Many Thanks it works great now.

---

### Post by yochaigal on 2014-04-18
I've just setup grub4dos/easy2boot on a FAT32 filesystem, but I am unable to fix non-contiguous files/defrag the filesystem using defragfs or defrag (a similar but bash-based script from  [http://ck.kolivas.org/apps/defrag/defrag-0.08/defrag](http://ck.kolivas.org/apps/defrag/defrag-0.08/defrag)). They both report no issues; if I go to a Windows PC with WinContig fragmentation is definitely detected.

Basically, has anyone found a way to truly defragment ISOs on easy2boot FAT32-formatted USB sticks from Linux?

Thanks

---

### Post by EnglishElectricAndy on 2014-05-02
I'm having some difficulty with this process. I end up with 'Missing operating system' when I reboot.

Should the command
```
sudo ./bootlace.com --time-out=0 /dev/sdb
```
be run whilst in the following subdirectory?
```
/grub4dos/grub4dos-0.4.6a/
```

Should the .iso files go in /EASY2BOOT/_ISO/MAINMENU/ or /EASY2BOOT/_ISO/LINUX/ ?

Edit: I'm using a SanDisk Cruzer 8GB USB

---

### Post by steve63752 on 2014-07-31
0.4.6a is Alpha and experimental - use latest version of 0.4.5c

[www.easy2boot.com](www.easy2boot.com) has all information

---

### Post by steve63752 on 2014-07-31
defragfs (perl) is included in latest download of easy2boot  v1.53  or 1.54Beta  [www.easy2boot.com]("http://www.easy2boot.com") - see \_ISO\docs\linux_utils - should work with FAT32

---

### Post by SuperFreak on 2014-07-31
Easy2Boot v1.42+ has a new feature that means that you don't have to make all your ISO files contiguous.
 
If the ISO is not contiguus, E2B will copy the contents of the whole ISO to the \_ISO\CONTIG.ISO file which is a contiguous file. E2B will then boot from CONTIG.ISO instead of the original ISO file.
 
However, this feature is only useful for .ISO files that are reasonably small as it takes time for E2B to make a contiguous copy of the ISO (and it does this each and every time you run the same ISO).

Read more: [http://www.easy2boot.com/not-contiguous-error/contig-iso/](http://www.easy2boot.com/not-contiguous-error/contig-iso/)

[http://www.easy2boot.com/not-contiguous-error/contig-iso/]("http://www.easy2boot.com/not-contiguous-error/contig-iso/")

---

### Post by steve63752 on 2014-08-02
v1.54Beta has a fmt.sh script which will format a USB drive partition, copy over the E2B files and run bootlace to install grub4dos to the MBR.
Use it at your own risk!

---

### Post by violetgirl on 2014-08-08
Many Thanks it works great now.

---

