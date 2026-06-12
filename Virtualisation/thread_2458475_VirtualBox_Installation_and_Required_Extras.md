---
title: "VirtualBox Installation and Required Extras"
date: 2021-02-25
forum: Virtualisation
---

### Post by kesetyan on 2021-02-25
Hi,

I am running Xubuntu 20.04.2 from an external usb hdd.  This has proved reliable and allows me to dual boot it with Linux Mint 20.1 which is installed on the desktop computer to which the hdd connects.

I have a Canon Canoscam 4200F flatbed scanner, which although old, works well.  However there are no drivers for Linux.  I can run it from Windows 7 which I have dual booting with Linux Mint on another desktop but would like to have it available in the other system.  I have an installation cd of Windows XP Professional so tried installing VirtualBox and adding XP to it.  That worked to a point but I obviously had missed something because I could not get XP to find the scanner which was connected by usb cable (the Canon drivers and software had been successfully installed into XP).  Also I could not move any data files between the guest operating system (XP) and the host (Xubuntu).  In addition XP did not recognize any usb memory sticks - it did recognize the desktop DVD drive from which XP had been installed and it allowed me to read data files from cds and dvds but not to edit them or use drag and drop.

I had found things a bit confusing from the beginning so it is very likely I've missed something important.  I installed VirtualBox via the Synaptic File manager where I found several VirtualBox related items listed and believe I installed the following three which I thought were necessary: virtualbox 6.1.16 base binaries, virtualbox-ext-pack 6.1.16 and virtualbox-qt 6.1.16 qt based user interface.  Since having only partial success with my virtualbox installation I removed it completely from my system via Synaptic and cleared residue manually.  I would like to have another go soon so would appreciate advice.  I want to be able to run XP Professional (with networking/internet disabled of course), be able to run my scanner and be able to move and edit data files between XP and the host system.  Hopefully this is possible if I install the right components and set up VirtualBox appropriately.

Thanks.

---

### Post by tea for one on 2021-02-25
You will need to install [COLOR="#0000FF"]Virtual Box Guest Additions[/COLOR] after you have created the VM

[https://www.virtualbox.org/manual/ch04.html#guestadd-intro](https://www.virtualbox.org/manual/ch04.html#guestadd-intro)

---

### Post by howefield on 2021-02-25
Thread moved to the "*Virtualisation*" forum.

---

### Post by SeijiSensei on 2021-02-25
I follow the instructions on the VirtualBox site to use the Oracle repository.  My installation is always up-to-date, and I don't have issues with compiling the kernel module.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

The current Extension Pack is here: [https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack](https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack)

---

### Post by kesetyan on 2021-02-25
Hi All,

Thanks for the replies.  

I've had another go and I did use Synaptic again as I did this before seeing your advice '[[COLOR=#000000]SeijiSensei'[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")[COLOR=#000000].  I installed [/COLOR]virtualbox 6.1.16 base binaries, virtualbox-ext-pack 6.1.16 and virtualbox-qt 6.1.16 qt. After I installed XP I installed VirtualBox Guest Additions as advised by you  '				 				 					 						 	[[COLOR=#000000]tea for one[/COLOR]]("https://ubuntuforums.org/member.php?u=585392")[COLOR=#000000]'.  I am now stuck at this point as I cannot fathom out how to manage settings to allow communication between the host system and XP in the virtual system so that I can move and share datafiles.  I have not yet installed the Canon drivers for the scanner as I suspect that there is more I need to do to enable XP to recognize it is plugged in and on. 

I've looked online for advice but what I find is difficult for this near eighty year old to follow.

@howefield thanks for moving my original post to this more appropriate forum.  Sorry I did not notice 'Virtualisation' in the listed forums - I was looking for 'Software', couldn't see that and chose 'General'.
[/COLOR]****

---

### Post by ajgreeny on 2021-02-25
You need to install the guest additions in the VirtualBox system itself, then after booting to XP go to the Devices menu of the guest window and choose "Insert Guest Additions CD" or similar words.
That should open up a dialogue in XP asking if you want to install the additions.  Follow the prompts to do so then reboot XP.
In the rebooted XP you will again need to go to the Devices menu -> USB and look for the scanner in the list of USB devices available.

---

### Post by kesetyan on 2021-02-26
Thank you ajgreeny - I've tried what you have suggested but I am still struggling.  As yet I have not added any software or drivers to XP so I have not attempted to test the scanner.  I am still trying to get VirtualBox to communicate with the host system and external usb storage connected to the host.  One thing I tried that did work was to do a screenshot of XP via the 'View' dropdown menu and 'Take a screenshot'.  That process opened the host file system window and allowed me to select a location for the snapshot within the host.  What I cannot yet do is create a file within XP and save it or copy it to a host folder.  If possible, I would like to see all connected usb devices and the host system listed in the 'My Computer' window in XP.

---

### Post by SeijiSensei on 2021-02-26
If you have the Extension Pack installed, you'll have access to "Shared Folders" in the Settings for the virtual machine. It will allow you to specify a directory on the host machine that you can access from the virtual one.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

I've found USB connectivity pretty hit or miss.

---

### Post by ajgreeny on 2021-02-26
> **SeijiSensei said:**
> If you have the Extension Pack installed, you'll have access to "Shared Folders" in the Settings for the virtual machine. It will allow you to specify a directory on the host machine that you can access from the virtual one.

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

I've found USB connectivity pretty hit or miss.
^^^^+1^^^^
This is one of the several reasons why I have now stopped using VBox apart from an old and very occasionally useful VM of Windows XP 32 bit which will not run in KVM/QEMU.  What little I know of Windows 10, which is very little as I no longer use Windows, it is much speedier in KVM than VBox; in the latter I found it almost unusable when trying it using the totally legal method to test Windows as a VM shown at [https://easylinuxtipsproject.blogspot.com/p/virtualbox.html](https://easylinuxtipsproject.blogspot.com/p/virtualbox.html). I later converted that downloaded .ova file to a qcow2 file which is the KVM/QEMU VM filetype and it's that which I boot occasionally just to remind myself how great it is to be using Linux.

In order to get full screen, USB and shared folders to work in VBox you must install the guest additions from the extension pack which you added to the VBox application, into the guest.  Without that being done, none of those things will work at all.

For all other VMs I now use KVM/QEMU which is a great deal faster and smoother running with fewer of the problems of that I did find in VBox.
There is no need, using KVM/QWEMU, to have additional utilities to get shared folders, USBs, etc, etc, to work. For shared folders I now use ssh between host and guest or vice-versa which is much better and I think is more secure.

---

### Post by kema77 on 2021-02-26
A good way to share files between host and guest is to set up a shared folder from the settings menu for your XP VM within the Vbox Manager.  However you must first enable sharing for the host directory that you want to share. That can be done from the right click menu in Ubuntu. (right click on the desired directory, select 'properties' and then 'Local Network Share') You do not have to give it the same permissions that I did here. You might be prompted to install additional files. 
[ATTACH=CONFIG]288018[/ATTACH]
   

Then from the settings menu in the VirtualBox Manager for the XP machine choose 'Share Folders'. Choose the folder that you just enabled sharing for. You can leave the mount point blank. The VM should auto-mount the directory and have it appear under "Network" in Windows Explorer.  Enable auto-mount.
[ATTACH=CONFIG]288017[/ATTACH]

Finally, you might have to restart the VM. 

This procedure worked for me with Ubuntu 18.04 as host  and Windows 7 as guest. I installed Virtualbox using Oracle's Ubuntu version.

---

### Post by kesetyan on 2021-02-26
Hi kema77,

Thanks for your useful input.  Slowly I am making progress.  Following your advice I have now been able to create a shared folder.  The method was an adaption of the advice you gave because in my Xubuntu 20.04 system (with the XFCE desktop manager) the folder right click menu does not include 'local network share' - however within 'Permissions' I was able to set 'read and write' for all users which seems to have done the trick.

It would be nice if I could get usb devices working so easily but for data storage, at least, I can now use my shared folder in the host system as a midway house.  It remains to be seen if I can get the scanner operating.  I know I can install the driver and related software in XP but will I be able to get XP to recognize when the scanner is connected via usb?

Thanks to all of you who have come to my aid: I've got to the point now where it seems worthwhile to install some of those old MS programs that have been stored away for a few years and I look forward to that.  If I can get the scanner working that will really be the icing on the cake.

Cheers.

---

### Post by kema77 on 2021-02-26
I assume you have guest additions and the extension pack already. With the VM powered off, select a USB controller from the settings>USB menu.  From settings>storage you can attach the PC's optical drive to the VM. Then use your driver CD if you have one to install the scanner software. (I'm not sure if this step is necessary if XP comes with a driver, but it can be installed that way if you must. It worked for me when installing a printer driver and related software that I wanted to run from my Windows VM.) In any event, it sounds like you have that worked out already anyway based on your last post.

Then with the the scanner plugged in to the PC and turned on, and the VM powered on, from the Virtualbox Manager machine settings select 'USB'. Then on the right side where you see the USB icons, left click on the second one from the top (with the + over it) for adding a new USB filter for devices that are attached to the PC. See if the scanner shows up. If so, click the box.

[ATTACH=CONFIG]288020[/ATTACH]

---

### Post by kesetyan on 2021-02-27
Thanks Kema77,

I found installing software via the dvd drive a problem so cheated by copying the appropriate files to a shared folder (I've now set up several thanks to your advice) and installed from there.  I puzzled as to why XP wouldn't let me install direct from the CD as with my first attempt at installing VirtualBox there was now problem and the installation started automatically.  I will update on my progress either later today or tomorrow after trying what you have advised regarding the scanner.

Cheers.

---

### Post by kesetyan on 2021-02-27
UPDATE:

@kema77,  Your helpful advice has enabled me to get XP to recognize the CD/DVD drive so I was able to install the scanner driver and software.  Unfortunately I am still having problems with USB and I have been unable to get XP to recognize any usb devices including the scanner, memory sticks, an old usb floppy drive and card reader.  It looks like I may have to give up on the scanner as my experience would seem to match SeijiSensei's comment "I've found USB connectivity pretty hit or miss".  Perhaps the usb drivers in XP are just not suitable for the host's usb system.

XP is too old to for my printer so I will always have save files to a shared folder print files via the host system.

Unless there is some sort of solution for my usb woes, I will mark this thread partially solved.  Not the perfect ending but nevertheless this has been a worthwhile learning situation for me and I am in a far better position than I was before I opened this thread so thank you kema77,  ajgreeny and SeijiSensei.

Just in case one of you can guide me to resolve this usb issue, I will not uninstall the scanner driver etc. for the time being but will do so later to save space if there is no possible resolution.

Cheers.

---

### Post by kema77 on 2021-02-27
Sorry to hear that kesetyan. I am no expert by any means and probably got in over my head trying to help you. I will just leave this link as my last gasp. I forgot about the need to add yourself to the vboxsf group. But then maybe you have already tried that. Good luck.

[https://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers-to-enable-usb-usage](https://askubuntu.com/questions/377778/how-to-add-users-to-vboxusers-to-enable-usb-usage)

---

### Post by kesetyan on 2021-02-28
Hi kema77,

Whether or not you are an expert your help has been invaluable.  Unfortunately I still cannot get the XP guest to recognize usb connected peripherals so it looks like my wish to use my old Canon scanner will not be fulfilled.  However there are plenty of things I can do with the virtual system including running ancient software so I feel quite positive about it all.  The scanner does work with my Windows 7 system which I have dual booting with a Linux OS on another desktop so the issue is not crucial and I can run Windows software not compatible with Windows 7 and later on the other desktop now.

I don't know if the usb problem is any way related to the fact that the host system is itself booting on a usb external hdd.

It's time to mark this thread as partially solved - thanks again for your help and persistence, it was all very much appreciated.

Cheers.

Update: Apparently I cannot mark it 'partially solved' so it will now show as solved.

---

### Post by CelticWarrior on 2021-02-28
> [COLOR=#000000]I don't know if the usb problem is any way related to the fact that the host system is itself booting on a usb external hdd.[/COLOR]


I isn't.
What happens exactly when you pass the scanner to the guest OS? The comment above - "[COLOR=#000000]I've found USB connectivity pretty hit or miss" - is mostly about USB storage devices, peripherals usually work. Once passed to the guest they should behave exactly the same as if connected to a bare-metal installed OS.[/COLOR]

---

### Post by kesetyan on 2021-03-01
Hi CelticWarrier,

Thanks for your interest.  When I try to pass the scanner to the guest operating system by using 'Select source' in 'Import' in my 'PhotoPlus' software, I get an error message 'There are no twain devices available.'  If I run the Canon Toolbox software I get the error 'Unable to open Twain source,. Please check connection then restart Toolbox.'  The connections are fine but when I check the 'Device Manager' in XP no usb controller drivers are installed.  XP is deliberately not connected to the internet and seemed unable to find the drivers on the installation cd.

---

### Post by CelticWarrior on 2021-03-01
Not entirely unexpected that you don't understand what passing a USB device to the guest means.
It is a Virtualbox feature: [https://forums.virtualbox.org/viewtopic.php?f=35&t=82639](https://forums.virtualbox.org/viewtopic.php?f=35&t=82639)

Please understand that you need to select the device to use via a Virtualbox menu before you can use it in the guest OS. By default a VM works only with the basic set of (virtualized) hardware. USB devices are in use by the host OS at all times until the user selects them to be passed to the guest OS.

---

### Post by kesetyan on 2021-03-01
Hi CelticWarrior,

This is proving rather more complicated than I first imagined.  Thanks for the link - It's a bit difficult to understand but I will work at it.  I do have some preliminary questions though:
1 - How do I select the device in a VirtualBox menu?  
2 - Which menu? 
3 - The section in your link on usb filters (usb filters section 3) and the text box to complete - I don't know 'Vendor ID' or 'Product ID' so where do I get that information?
4 - I've uninstalled the Canon drivers - should I reinstall them in XP before attempting the above?
5 - Should select the device in the VirtualBox menu with XP unloaded?
4 - Both my desktop computer and my external hdd Xubuntu system are 64bit whereas my XP installation is 32bit, would this have any impact on what I am trying to do?
5 - I'm not sure if I have an option to choose 64 bit on my installation cd, if I have (and I was considering doing a fresh install of XP to tidy things up), would that be advantageous?

Sorry if I seem a bit clueless but this is very new to me.

---

### Post by CelticWarrior on 2021-03-01
The menu is [COLOR=#333333][FONT=&amp]Devices » USB » ... exactly as mentioned in the on-the-fly section of the instructions, which is the method you want to use.

The main thing to understand here is what a VM is, how does it work and how it handles hardware. A VM uses for the most part a virtual CPU (one or more cores from the real one), part of the RAM, a virtual graphics subsystem and a virtual drive, that's it. Just because the VM is running doesn't mean it can access and use the stuff connected by USB. As a matter of fact, this is exactly the beginning of the instructions:
[/FONT][/COLOR]> [COLOR=#333333][FONT=&amp]USB devices [/FONT][/COLOR][COLOR=#333333][FONT=&amp]**cannot be shared**[/FONT][/COLOR][COLOR=#333333][FONT=&amp] at the bus level. That means that two computers [/FONT][/COLOR][COLOR=#333333][FONT=&amp]*(a host and a guest)*[/FONT][/COLOR][COLOR=#333333][FONT=&amp] cannot share the same device. Think of it as having a USB stick, a printer, a webcam or a WiFi adapter hooked into two computers at the same time. You simply can't.[/FONT][/COLOR]
[FONT=Lucida Grande][COLOR=#333333]Unfortunately this whole discussion suggests your expectations were very different than what can be done in reality. No, in order to use the device in the VM it need to be "detached" (become unavailable) from the host OS first. The guide provides two methods, one transient via a point-and-click menu, and one "permanent" (as long as Virtualbox and that VM are running) that sequesters the device as soon as it detects it. The "permanent" way, via USB filter, does indeed require "Vendor ID" and Product ID". Those can be obtained with 'lsusb'. Example:
   [/COLOR][/FONT]```
Bus 001 Device 004: ID **0a12:0001** Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```
In the above example (Bluetooth USB dongle), the Vendor ID=0a12 and the Product ID=0001

[FONT=Lucida Grande][COLOR=#333333]Whether or not you should have the drivers/software already installed I don't know but it should be the exact same way as in a bare-metal installation. When the device is passed to the guest via Virtualbox menu that is exactly the same as connecting the device in a normal installation, the (guest) OS behaves the same indicating "new hardware found", plays a sound, etc.
[/COLOR][/FONT]32-bit or 64-bit doesn't matter unless the required drivers/software only run in one or another.

[FONT=Lucida Grande][COLOR=#333333]If this is hard to understand - it shouldn't be... - then consider using supported hardware instead. Only you can know how valuable your time is. I certainly wouldn't have spent even half of that just to make a piece of museum work.[/COLOR][/FONT]

---

### Post by kesetyan on 2021-03-01
Hi CelticWarrior,

Thank you for your patience and the time you have given in helping me.  I guess I'm a poor student but at nearly eighty years old perhaps I can plead senility.  I've made some progress following your advice in that I now have the scanner and a usb memory stick listed in the usb filter settings but as yet I am not able to access them in XP.  

I would fully understand if you feel you cannot take this any further with me and really I am quite happy in getting as far as I have with VirtualBox.  I take your point that using outdated, unsupported hardware is not an efficient use of time but for me this is a bit of a personal challenge and it help keeps my brain active in these times of covid lockdown. 

I'm sorry that I find it hard to understand - I'm generally not too bad at working things out but this is a new concept for me so progress comes in small steps rather than giant leaps.  It might be time to call it a day and stick with things as far as they have come but please understand that I am very grateful for the help I have received from you and the others who have come to my aid.

Cheers.

---

### Post by kesetyan on 2021-03-02
UPDATE:

Thanks to the help and encouragement I have received on this forum especially from kema77 and CelticWarrior, I have resolved the issue with the scanner and learned fair bit en route.  The issue was mainly caused by my incompetence and lack of understanding (both aspect improving a little after the experience).  It does seem that the guest operating system (XP professional SP3) had trouble with the USB3 ports on my computer where it recognized plugged in items but failed to load them.  The USB2 ports are OK so I can do all I was hoping to be able to do at last.

Cheers.

---

### Post by Paulgirardin on 2021-03-03
I find Gnome Boxes much easier to set up file and USB sharing on. Just install Spice Guest Tools on the guest OS.
I have used both Virtualbox and Boxes, Boxes is less confusing,Vbox allows you to export the appliance to make reinstallation simple.

---

### Post by kesetyan on 2021-03-04
Hi Paul,

Thanks for your input.  I'll have a look at Gnome Boxes but while I have VirtualBox doing everything I require, I shall keep that on the system. 

My guest system, XP Professional SP3, is working well and I've installed some of my old software although there were registration problems with some where original registration keys no longer work.  Fortunately I was able to find alternatives without registration key requirements including Libre Office 5.1 which is old enough to be compatible but new enough to read and write to most office files such as xlsx and docx.

My original scanner problem, now fully resolved, was worsened by the fact that a couple of usb leads had iffy plugs so contact was erratic.  Those leads have been replaced by reliable alternatives.  One pleasing thing I have noticed is that although XP is running in a VM, it is quicker than it used to be when installed directly in the original desktop computer which became defunct and stripped down several years ago.

Cheers

---

### Post by kema77 on 2021-03-04
> One pleasing thing I have noticed is that although XP is running in a  VM, it is quicker than it used to be when installed directly in the  original desktop computer

Your experience inspired me to find a legit iso of XP and fire up my own VM. I too was pleased at how snappy it booted and ran. No USB issues either.:P

>  I've installed some of my old software although there were registration  problems with some where original registration keys no longer work.

Interesting. My old version of Word (2000) accepted the product key. Haven't tried Excel 97 yet. But you are right, Libre Office is a fine alternative.

---

### Post by kesetyan on 2021-03-04
@kema77,
I'm learning more by just playing with the VM and am certainly rather more confident than I was this time last week.  I don't intend overloading XP with software although I have set up a folder for several portable applications and those I've added are working well.

@Paulgirardin,
First impressions of Gnome Boxes are encouraging save for one problem, I cannot get XP Professional to install either directly from the installation cd or from an iso file.  However there are plenty of Linux distributions to explore so I may hang on to it for testing so of those in a virtual environment.

---

### Post by kesetyan on 2021-03-04
Hi,
Well I've given Gnome Boxes a brief trial and have decided it is not for me - I much prefer VirtualBox.  My question now, which perhaps should be posed in a new thread, is what is the best way to get rid of Gnome Boxes completely.  I'm reasonably competent using the terminal and familiar with terms like purge etc. in removing software but don't want to make a mistake.  Would "sudo apt-get remove --purge gnome-boxes" do the trick?

---

