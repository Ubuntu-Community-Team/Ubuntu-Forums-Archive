---
title: "Unable to install Win7 - &quot;The selected disk is of the GPT partition style&quot;"
date: 2013-05-21
forum: System76 Support
---

### Post by ebeyer on 2013-05-21
I'm trying to install Win7 on my Bonobo extreme per the instructions on the knowledge76 site: [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine](http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine)

I get as far as the step "Make sure that the new partition is selected. then click Next." but the Windows installer says "Windows cannot be installed to Disk 0 Partition 3. (Show details) --> Windows cannot be installed to this disk.  The selected disk is of the GPT partition style".

I spent about three hours googling around.  I tried to follow the directions here: [http://ubuntuforums.org/showthread.php?t=1856987&page=3](http://ubuntuforums.org/showthread.php?t=1856987&page=3), which purports to allow you to convert the desired windows partition to MBR but Windows 7 refuses to install to it.

I've even contemplated wiping the drive, installing Windows and adding Ubuntu back as the second OS, but Windows doesn't even give me the option to do that.
I'm not excited about virtualization, unless it's a last resort (because part of what I want Win7 for is for games that don't play nice with virtualization).

I am using the 64-bit version of the installer.  I have tried enabling the UEFI, which resulted in not being able to boot the Windows install disk at all.

Am I doing something basic/silly that is wrong (apart from using Windows at all)?  A practical solution would be very much appreciated.

Respectfully, 
EB

---

### Post by oldfred on 2013-05-22
Windows only installs to gpt partitioned drives with UEFI. Then Ubuntu also needs to be UEFI, but Boot-repair can convert install to use grub-efi in place of grub-pc, if in BIOS mode now.

Or you can convert drive to MBR, but get into the 4 primary partition limit. You will need gdisk.
If in BIOS mode Windows has to boot from a primary NTFS formatted partition with the boot flag.
IF gpt the only partition with a boot flag is the efi partition which you can only have one per drive.

  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx]("http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx")
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)



       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by ebeyer on 2013-05-22
Thanks for the thorough reply.  Unfortunately, there is much of what you patiently explain that is safely over my head.  I humbly submit that the good people at System76 need to incorporate what you are saying in their step by step directions.  Until then, I fear I will continue to fruitlessly spin my wheels.

Respectfully,
EB

---

### Post by oldfred on 2013-05-22
UEFI systems are new and more complex as they can be either UEFI or BIOS. And then drive may be formatted with newer gpt partitioning for use with UEFI or the 30 year old MBR(msdos) partitioning.

Instructions on System 76 site are for BIOS based install. 

If you system is UEFI, you have to convert Windows installer to flash drive and add UEFI capability as in posts above. Windows 7 standard DVD is for BIOS install only but can be copied to a flash drive.

---

### Post by ebeyer on 2013-05-22
I'm pretty sure UEFI is turned off.  My BIOS only lets me turn it on if the OS I'm running is Win8.  I tried turning it on, in fact, but the Win7 DVD wouldn't boot.  BIOS install fails as per my original post.  Win7 installer doesn't give me the option of wiping the drive and installing just Windows, either.
EB

---

### Post by oldfred on 2013-05-22
Best to see detail. But I may not be back for two weeks.


 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ebeyer on 2013-05-22
Forgive me as I stumble through the details.

I used boot-repair to fix grub after the windows installer managed to screw it up a couple of times during my earlier attempts to start the windows install.  I used the recommended repair with success each time.  I'm hearing you suggest that I use the advanced option to "restore" the MBR of my desired windows partition (/dev/sda3), after which Win7 should allow me to install the OS to that partition normally.  Is that true?
EB

---

### Post by oldfred on 2013-05-22
It depends on whether you are in BIOS mode or UEFI mode.
Windows will only install in UEFI mode when drive is gpt partitioned. So if you have Windows 8 pre-installed drive is gpt. Ubuntu will boot from gpt partitioned drive with either BIOS or UEFI. But you would only be able to install Windows 7 if you erase drive and convert it to MBR. Or convert Windows 7 installer to flash drive with UEFI install capability.
If you erase drive, I would  backup entire drive as you may never be able to reinstall Windows 8.
If you use Windows 7 to erase drive and install in MBR, then it does not erase backup gpt partition table (one of gpt's advantages) and you have to use fixparts to remove the backup gpt data.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

    

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by isantop on 2013-05-22
I believe he'll need to reinstall Ubuntu with an MSDOS disk. We don't have UEFI firmware on our systems.

---

### Post by ebeyer on 2013-05-22
I'm confused.  Assuming I don't want to wipe my Ubuntu partition, I hear you saying I can use a windows 7 thumb drive install and UEFI to install on the partition I created (/dev/sda3).  But the last poster, from System76 is saying there is no UEFI support on their laptops?  But there's an option in the BIOS to select Win8 as the OS and to turn on UEFI.  Is that something else?

So assuming I can't boot the Win7 UEFI install, either as DVD or as a flash drive on my System76 laptop, then you're saying my only option is to boot under BIOS, which means wiping the drive, installing Win7 and rebuilding Ubuntu after that.  Am I understanding this correctly?

If so, are there instructions (assuming you haven't already linked this, in which case I apologize) that will show me how to get the Win7 install disk to install on my hard drive that already has Ubuntu installed and has no MBR?

Thank you again for your patient explanations.
EB

---

### Post by oldfred on 2013-05-22
I do not know about System76 system.
They may just be using gpt partitioning with BIOS as that is how I boot my system which does not have UEFI capability. 
But Windows only installs to gpt with UEFI. If you do not have UEFI, and you really want Windows you have to totally erase drive and start from scratch. You will have to use fixparts also as posted above.

---

### Post by isantop on 2013-05-22
Can you take a picture of the option in the BIOS you're referring to? There shouldn't be such an option on our systems.

In any case, switching to UEFI will require reinstalling Ubuntu. Switching to an MSDOS disk will also require reinstalling Ubuntu.

---

### Post by bakelitedoorbell on 2013-05-24
I think you may be overcomplicating this.  Windows 7 wants to be the first OS on your hard drive.

Back up your Ubuntu data, wipe the drive, install Windows, repartition and intall Ubuntu.
If Windows won't erase the drive then use a Ubuntu LiveCD to wipe it.

---

### Post by isantop on 2013-05-24
Windows (7 at least) has no preference where it lives on the drive, and we've had several test installations with Ubuntu coming before Windows.

The issue ebeyer was having is that our systems come with GPT partition tables and a traditional BIOS firmware. Windows will only install to a BIOS system if the disk is MSDOS, or to a GPT system if it uses UEFI. Not both.

We are looking at switching to UEFI boot methods for future models.

---

### Post by bakelitedoorbell on 2013-05-24
> **isantop said:**
> Windows (7 at least) has no preference where it lives on the drive, and we've had several test installations with Ubuntu coming before Windows.


Apologies, I was not aware of that.  I had a similar problem myself last year with trying to install Windows7 after Ubuntu, and was able to solve it by installing Win7 first, then Ubuntu.  I had Grub set up to go into Ubuntu by default.  So my comment was based only on my own experience.

---

### Post by stranger1 on 2013-06-29
I had this problem too with my new 1 TB hard drive from Seagate. I had tried everything to be able to install Windows 8 on the new hard drive or even Windows 7…And of course I went into different websites trying to search for the answer and nothing really helped! Only on the Microsoft website it did say something about installing Windows XP. It was the last recourse I had. Luckily for me, I had an old copy of Windows XP Professional Service Pack 3. When installing Windows XP, I did run into the part that I needed to select the partition where I wanted to install the OS. I selected it and…it gave me the same error message, however, it did provide me with instructions as to how to resolve the issue. It said to go back and delete the partition and create a new partition. I did it. The GPT partition seemed to be raw data, even though I was able to save any type of files in the GPT partition. I performed a quick format of the new NTFS partition and there it was, the Windows XP Professional SP 3 succesfully installed in a previous impossible GPT partition!! And immediately after I installed the new Windows Blue [Windows 8.1] without a problem!! I hope it actually helps anyone else who has the same problems as I did!

---

