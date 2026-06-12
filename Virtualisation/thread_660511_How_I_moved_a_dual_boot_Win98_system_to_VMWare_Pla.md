---
title: "How I moved a dual boot Win98 system to VMWare Player"
date: 2008-01-06
forum: Virtualisation
---

### Post by gilf on 2008-01-06
I just completed two conversions of Windows 98SE systems from dual boot to VMWare Player virtual machines.

While I've read many threads on creating new virtual machines from fresh Windows installs, I wanted to move my old windows partition into VmWare, without having to reinstall all of the software I've collected over the years.

In many cases this saves having to contact software providers for new installation keys, and saves tons of installation work. The VMWare Conversion It's not a piece of cake, but the result is a system that looks and acts exactly like my old one.

Please note that this is a new virtual machine, not a redirection of VMware to the existing dual boot partition. There are threads elsewhere dealing with that process (and it has several serious drawbacks, noted in those threads).

With a new virtual machine containing the contents of the old windows partition there are many advantages -- portability, the ability to back up your entire install by copying one file, complete separation and protection of the original dual boot windows partition, no constant changes of Windows hardware profile (and possible overuse of the coa key), etc.

Because I was unable to find a single location which outlined the steps needed to copy a pertition into a virtual machine for VMWare Player, here is an overview of the steps I took to achieve it. (I realize this is sketchy to begin with, -- not quite a How-To,  but I will flesh it out in subsequent posts, links,  and edits -- I just want to get this down now in case it helps someone who needs the general strategy I used, right now. I also had many problems to solve along the way, and I'll try to steer you around them with this strategy)

My overall process finally amounted to this:

1.) Download and Install VMWare Player from the VMWare website.
2.) Install Partimage through Synaptic
3.) Download and burn a CD of the ISO of Parted Magic ( [http://partedmagic.com](http://partedmagic.com) )
4.) Optional: Download a copy of VMWare tools ( *[COLOR="Red"]see link in later post, below[/COLOR]*)
5.) Download a set of VMDK empty machines of various Gigabyte sizes from John Bokma ( [http://johnbokma.com/vmware-player/vmdk.zip](http://johnbokma.com/vmware-player/vmdk.zip) )
6.) Create a folder named **VMWare** in your home directory
7.) Using a text editor create a file named **Windows98SE.vmx** like the one I used as follows:

> #!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Windows98SE.vmdk"
memsize = "[COLOR="Red"]256[/COLOR]"
MemAllowAutoScaleDown = "FALSE"

# Settings for first physical CDROM drive
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"

# Settings for second physical CDROM drive
#ide1:1.present = "TRUE"
#ide1:1.deviceType = "atapi-cdrom"
#de1:1.startConnected = "TRUE"
#ide1:1.fileName = "auto detect"
#ide1:1.autodetect = "TRUE"

floppy0.present = "FALSE"

ethernet0.present = "TRUE"


usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows 98SE"
guestOS = "win98"
nvram = "Windows98.nvram"
MemTrimRate = "-1"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"
uuid.bios = "56 4d 5c cc 3d 4a 43 29-55 89 5c 28 1e 7e 06 58"
ethernet0.generatedAddress = "00:0c:29:7e:06:58"
ethernet0.generatedAddressOffset = "0"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""

[COLOR="Red"]Note, change the memory figure (in red above) to *a maximum* of half of your total memory - Win98 will run well in 128 Megs [/COLOR]

8.) save that file in your new VMWare directory

9.) Decide how large you want to make your Virtual machine (in Gigabytes). Think about your needs. I decided that since I would mainly be using Ubuntu from here on out, and the Windows machine was only for "must-use" occasions, I was going to give myself 5 Gigabytes on one of my machines and 20 gigabytes on another heavily programmed one. The machines will reside in .vmdk files -- so pick an appropriate sized one from the zip file downloaded in step 5.) and move it to your VMWare folder.

10.) Rename your .vmdk file to Windows98SE.vmdk

11.) You will need an external hard drive or DVD drive or a memory stick to hold an image of your Windows installation while you transfer it to the .vmdk file. It needs to be large enough in capacity to hold your windows installation. If you first de-fragment your windows partition (using windows defragmenter) it may be possible to shrink it using a proprietary windows partition manager, Ranish PM, or Gparted -- be careful if you do this and know what you are doing. Always back up first before operating on any partition. If your partition is larger than the capacity of a DVD drive, Partimage can span disks to create a multi disk image. You could even use a CD burner for this, though it may result in many disks for a large system. An external Hard drive is ideal, as it is likely to be big enough to easily handle a partiton image.

12.) in a terminal open partimage
>  sudo partimage

Suggestions while generating an image file in Partimage:
 -- use the <tab> key to move between lines, <space> to check a check box, F5 to move to next page
 -- highlight the Windows partition you want to copy to an image file
 -- make sure you are saving a partition to an image file
 -- save as something like **sda1/Windows98SE.partimg** (if your external hard drive is mounted as sda1)
 -- I suggest saving the image* uncompressed* if you have the space -- why? Because Partimage choked for me when restoring a zipped file over 4 Gigs in size. Subsequent web searches revealed it's a bug. You may be able to zip a file under 2 gigs and have it restore however.
 -- if you don't need to span multiple CD or DVD disks with a very large file, set the spanning size to automatic

13.) Close partimage. When the image file is finished, it will probably have an extension like ".000" added. That isn't a problem unless you compressed the file, in which case you should change it to an appropriate zip extension (like .gz) for the zip type you used.

14.) Put the Parted Magic CD in your* internal* cdrom drive. 

15.) Double click on the **Windows98SE.vmx** file in your **VMWare** folder. This should start VMWare player, and should also start it booting from the Parted Magic CD.

16.) Once in Parted Magic click on the Partition manager (left icon at bottom of screen).

17.) Partition the new virtual drive as FAT 32. You will have to do this in 2 steps as you will first need to set a volume label -- say yes to the default. Close partiton manager when done

18.) In the right fly-up menu select the Mount manager and mount your external drive.

19.)  Open the terminal and type
>  partimage

20) Restore your saved image file to the new virtual partition.

21.) Open Partition manager again and set the flags for the new partition to **boot** and** LBA**

22.) Your partition will almost certainly be larger than your image was -- so we need to correct the disk partition data for Windows to recognize the new size. Run the **Check** process in partition manager to correct the size of the partition.

23.) Click Quit in the upper left of the VMPlayer window.

24.) Put your Windows 98 CD in your internal CDRom drive -- you will need it to install many drivers to support the new virtual machine. You won't be installing Windows, it's already there, but your VMWare virtual machine has some new virtual devices and they require drivers found on the CD.

25.) Again start Your VMPlayer by double clicking on the **Windows98SE.vmx** file in your **VMWare** folder.  This will boot the Win98 CD, which inturn will give you 2 choices in a menu.  Boot from HD or from CD. Choose HD -- if not hilighted already.(Note:  If you wan to type a choice 1 or 2 you have to first click on the VMPlayer window to enter it, and you have to be very quick about it in a fast modern machine! It goes by quick!)

26.) Once your machine boots in HD mode windows will prompt you for driver locations. Most of these will be on the Windows 98 CD (**D:\Win98**). I found I had to locate a few after the initial install (which were not on the CD) by doing a search in Windows for the filenames, then re-installing the particular devices drivers with that information (Settings>System>Device Manager> disabled devices). You can also look on the net for a driver file if you can't find it elsewhere. You may need to re-boot the virtual machine a few times when instructed, to install various drivers.

27.) VMPlayer  Windows 98 virtual machine should be working, but only with 640 x 480 resolution --and in a shaky manner at that. Have no fear. Now move VMWare Tools into the virtual machine, unzip them into a folder and run the setup program. This will install an SVGA virtual graphics card as well as speed up and smooth out the entire machine so that it feels like it is working in native mode.

You're done, enjoy your new capability.

Additional helpful references:

1.) VMX File reference: [http://sanbarrow.com/vmx.html](http://sanbarrow.com/vmx.html)
2.) Running a native partition in VMPlayer [http://ubuntuforums.org/showthread.php?t=380699](http://ubuntuforums.org/showthread.php?t=380699)
3.) How to install a new WinXP install in VMPlayer [http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html](http://johnbokma.com/mexit/2005/10/26/vmware-player-windows-xp.html)
4.) Also: [http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

---

### Post by Shazaam on 2008-01-07
Have you tried this site yet for making blank VMware Player vm's?.....

[http://www.easyvmx.com/](http://www.easyvmx.com/)

Takes less than 5 minutes to make one.

---

### Post by gilf on 2008-01-07
Shazaam,

No I haven't, though I'm sure it's an easy way to do it if you have a defined purpose that doesn't change. I'm glad you added this.

I found however that I wanted to be able to read and understand VMX files, because I was frequently tweaking the same file  while setting up and exploring my system and its capabilities, and while troubleshooting

The first reference I listed above does a great job of providing examples and explanations for the various pieces and commands of a VMX file. I found it after spending a lot of time guessing and hunting down other example vmx files and comparing. The site I list in the reference was a goldmine of information, finally explaining the mysteries.

---

### Post by gilf on 2008-01-07
I just tried the EasyVMX method and it's very nice.
It creates the .vmdk file, too, so you don't have to download one.

This would replace steps 5 and 11 abovbe.

---

### Post by gilf on 2008-03-07
Here's a link to a how-to for obtaining VMWare Tools:

[http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html)

---

