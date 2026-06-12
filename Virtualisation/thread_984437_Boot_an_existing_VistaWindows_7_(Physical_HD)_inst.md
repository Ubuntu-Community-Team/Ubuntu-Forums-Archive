---
title: "Boot an existing Vista/Windows 7 (Physical HD) install with VirtualBox"
date: 2008-11-16
forum: Virtualisation
---

### Post by canabal on 2008-11-16
Credit for this all goes to Sand Lee, who put in all the effort and troubleshooting. That guide on XP is located [here]("http://ubuntuforums.org/showthread.php?t=769883").  Much of this is copying what was done and just adding to it because of a lack of time on Sand Lee's part.

I have recently Upgraded to the Windows 7 beta (build 7000) and to Jaunty 9.04.  Using the same settings as before, this VM still works for me, I hope it does for you also.

[CENTER][SIZE=5]Introduction[/SIZE][/CENTER]
I re-made this tutorial based on Sand Lee's for XP, and used him additions to change it to Vista, so all credit goes to him, I am just posting this to make it easier to find for people.  I agree with him when he says VMware felt off, I could not get it to work personally, plus VirtualBox is Open Source.  Using a VM makes it much easier to boot into Vista if you need something quickly and do not want to exit your current session.  I did this with Intrepid Ibex, Ubuntu 8.10.
*[SIZE=1]Please read or skim the tutorial before attempting it. Note: This tutorial was tested to work with VBoxOSE 2.04 and may not work for users w/ SATA drives. [/SIZE]*

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=92913&stc=1&d=1226869553[/IMG]

[SIZE=4]Step 1: Create a grub boot cd[/SIZE]
Creating a grub cd will let you boot straight into your target Windows partition.[SIZE=1] 
**Following method adapted from [grub manual.]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD_002dROM.html")**[/SIZE]
```
 mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
```
This creates a copy of your current GRUB, so from here you configure **~/iso/boot/grub/menu.lst** to boot your target partition (~ is your home).
[LIST]
[*] Change the default option to your vista partition.
[*] Set the timeout at 1.
[*] If your vista partion says savedefault in the grub.lst be sure to delete that line.
[*] Then run the following to create the grub.iso file.[/LIST]
```
mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso
```

[SIZE=4]Step 2: Create a virtual disk (.vmdk)[/SIZE]
When creating such a disk, it's preferable to only specify your Windows partition. This is a safety precaution that will prevent a data corruption problem that results from booting into the currently running OS. As a preliminary step, you must add yourself to the disk and vboxusers groups,
```
sudo usermod -G disk,vboxusers -a `whoami`
```Log out and log back in here... and edit the following command to point to your WinVista partition: (I specified my WinVista partition - /dev/sda2 - with "-partitions 2") 
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
```

[SIZE=4]Step 3: Boot into Vista and disable hardware-specific and unnecessary start-up items in msconfig[/SIZE]
[LIST]
[*]Click Start > In Search Box type msconfig
[*]    Hit Enter key
[*]    Remove anything not necessary, some trial and error may be required if you are not sure what you need
[/LIST]

[SIZE=4]Step 4: Boot back into Ubuntu and create a VM with the settings below. If they don't work try switching settings.[/SIZE]
[LIST]
[*]Create a machine that uses the created .vmdk (in the drop-down menu of the HD selection section)
[*]   You may have to switch between the two IDE controllers types (Settings/Advanced) to see which works for you
[*]   Use the same MAC as your real network card for your virtual card if you experience network problems
[/LIST]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=93898&stc=1&d=1227472377[/IMG]

[SIZE=4]Step 5: Boot Vista in VirtualBox[/SIZE]
[LIST]
[*]    Realize that you may have to reactivate your copy of Vista
[/LIST]

[COLOR="Red"][SIZE=3]*** Do Step 6 at your own risk, some have had problems with it ***[/SIZE][/COLOR]
[SIZE=4]Step 6: Mount the Guest additions CD to install the VBox Drivers[/SIZE]
[LIST]
[*] You will have to mount your HDD for this so be careful and make sure to select your Vista partition.
[*] Image can be found [here]("http://download.virtualbox.org/virtualbox/2.0.4/VBoxGuestAdditions_2.0.4.iso").
[*] Do not install it directly into Vbox, only use it in Vista for finding the driver.
[*] Reboot Vista and install the Guest additions inside Vista for a better experience.
[/LIST]

[SIZE=4]Step 7: Mount network drivers CD to install drivers[/SIZE]
[LIST]
[*] Again be careful and select your Vista partition because you HDD is mounted.
[*] Download files and create ISO using the code below thanks to [Jhcore.com]("http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/")
```
cd ~/install_files
wget http://www.amd.com/us-en/assets/content_type/utilities/V4.51.zip
unzip V4.51.zip -d driver
mkisofs -o driver.iso -R -J driver
```
[*] Mount driver.iso in VirtualBox
[*] go to: Control Panel > Hardware and Sound > Device Manager. Right click on Ethernet Controller > Update Driver Software > Browser my computer&#8230;
[*] Navigate to the CDROM drive, and click ok.[/LIST]

[CENTER][SIZE=4][COLOR=DarkBlue]::: ::: [/COLOR][/SIZE]**[COLOR=DarkSlateBlue][SIZE=5]Troubleshooting[/SIZE][/COLOR]**[SIZE=4][COLOR=DarkBlue] ::: :::[/COLOR][/SIZE][/CENTER]

**More Troubleshooting: ](*,)**
[Migrate_Windows - Virtualbox]("http://www.virtualbox.org/wiki/Migrate_Windows")

**Sources & Helpful Links: :-\"**
[Sand Lee's Original Post]("http://ubuntuforums.org/showthread.php?t=769883")
[vboxforums-version]("http://forums.virtualbox.org/viewtopic.php?t=9697"),[squidoo-virt]("http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu"), [mazimi-virt]("http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/"), [mazimi-bypass]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/"), [mesbalivernes-virt]("http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html"), [Network Drivers tutorial]("http://jhcore.com/2007/03/25/vista-on-ubuntu-using-virtualbox/")


Comments and suggestions welcome!

---

### Post by canabal on 2008-11-16
[CENTER][SIZE="4"][COLOR="Green"]Updates[/COLOR][/SIZE][/CENTER]

Sand Lee made an edit using a grub boot CD so I edited mine to follow and ensure the same experience.

---

### Post by rkrishnam_can01 on 2008-11-17
Thanks for this tutorial canabal. I going to try this out in the next few days.
After these steps will Vista boot natively in a dual-boot mode as well?

Thanks

---

### Post by canabal on 2008-11-17
Yes it boots fine, what I recommend is you turn the timer off in GRUB and then put default position to 3.  For me, this means it will boot nothing, as it is on the text label about "Other operating systems".  This will save any errors of booting up into Ubuntu inside the VM and destroying your install.

---

### Post by JeyPeyy on 2008-11-18
Works good, but is there a way to get the graphics work properly so I can play games?

---

### Post by Sand Lee on 2008-11-22
> **JeyPeyy said:**
> Works good, but is there a way to get the graphics work properly so I can play games?

Virtualized graphics is a problem that hasn't yet been figured out with VirtualBox.

---

### Post by canabal on 2008-11-23
Updated to add GRUB boot CD.

---

### Post by anystupidname on 2008-11-25
Can somebody please confirm that once I set this up I won't have to continually re-activate Vista each time I boot it either natively or virtually? I intend to be able to boot it alternately virtually and natively continuously forever. Does that make sense? Does it somehow retain the previous hardware profile or how does that work since I keep reading Vista doesn't allow for multiple hardware profiles...?
Thanks!

---

### Post by Sand Lee on 2008-11-25
> **anystupidname said:**
> Can somebody please confirm that once I set this up I won't have to continually re-activate Vista each time I boot it either natively or virtually? I intend to be able to boot it alternately virtually and natively continuously forever. Does that make sense? Does it somehow retain the previous hardware profile or how does that work since I keep reading Vista doesn't allow for multiple hardware profiles...?
Thanks!
 No dice. You'll have to reactivate it everytime you switch back and forth. I'm actually about to work on a solution to this problem and I'll probably figure out if it's plausible by this weekend.

---

### Post by anystupidname on 2008-11-26
Thanks for the response. I look forward to your findings.

---

### Post by Sand Lee on 2008-11-27
I was going to attempt the method shown [here]("http://forums.virtualbox.org/viewtopic.php?t=11175&highlight=dmi") for bypassing activation, but lost the will :oops:
I've also got to study for finals - so whoever wants to try it, be my guest =P

---

### Post by bssdvr on 2008-12-06
This doesn't work for me, I have two problems:
1- the Grub image created is not booting and the grub installed on my ubuntu partition (the original grub) is trying to boot. Because I created my vmdk without the ubuntu's partition parameter, this brings a grub error 17, so I created a vmdk with my linux partition, then my /boot/grub/menu.lst boots (I reconise the parameters)... But I don't like this option.

2- even when i try to boot on vista with the original menu.lst, vista says that it can't boot, probably because of a recent hardware change...

I think that I can fix the 2nd problem by removing boot tasks on vista, but I have no idea about my first problem.

Thank you for your answers.

---

### Post by acebrain01 on 2008-12-07
So for my first post here. My vista is on it's own hard drive not on sda but sdb and i can not get grub to load it. also could only create passthru by sudo the command. any help would be greatly appreciated.

---

### Post by Natovr on 2009-01-05
Hi,
I get this error when following the steps in the first post. Part of the screenshot also shows the basic settings of the Vista VM...

My total memory is 2048MB, but 256MB is taken by the ATI 1250 graphics chip. The processor is 1.83 GHz Core 2 Duo, and the OS is Ubuntu 8.10 (Intrepid) 64-bit. Vista is 32-bit Home Premium. It's a Samsung R60+ Laptop, Vista is on /dev/sda1, with a data drive (mounted on Ubuntu aswell) on /dev/sda2.

It firstly comes up with a black screen, and when I send a shutdown signal, it comes up with this BSOD :|
thanks in advance :)

---

### Post by wrichtmyer on 2009-01-10
solved

---

### Post by wrichtmyer on 2009-01-10
bump help.

---

### Post by canabal on 2009-01-11
> **wrichtmyer said:**
> I get an error on the Grub menu INSIDE the VirtualBox saying:

Error 17.

Help please?


Is the only thing it says: "error 17"?

Or is there more to it?

---

### Post by canabal on 2009-01-11
> **Natovr said:**
> Hi,
I get this error when following the steps in the first post. Part of the screenshot also shows the basic settings of the Vista VM...

My total memory is 2048MB, but 256MB is taken by the ATI 1250 graphics chip. The processor is 1.83 GHz Core 2 Duo, and the OS is Ubuntu 8.10 (Intrepid) 64-bit. Vista is 32-bit Home Premium. It's a Samsung R60+ Laptop, Vista is on /dev/sda1, with a data drive (mounted on Ubuntu aswell) on /dev/sda2.

It firstly comes up with a black screen, and when I send a shutdown signal, it comes up with this BSOD :|
thanks in advance :)

Try unmounting the drive you are using for windows in ubuntu when you are running it (if you are not already doing that).

Otherwise I dunno, try the steps from the beginning, I know I had to a couple times to get it to work because I missed something.

---

### Post by wrichtmyer on 2009-01-18
Upon doing these instructions, I get past the GRUB and I recieved an: Error 18: Selected cylinder exceeds maximum supported by BIOS.

Help please?

There is another boot menu inside the Vista Partition. Yes, I unmounted Vista, too.

I'm running Windows Vista with 2746 MB of RAM (I have 4GB)
and with 32 MB Video Memory (I could do a maximum of 128MB)

VirtualBox is 64 bit, I believe, Ubuntu is 64 bit, and my Vista is 64 bit.

---

### Post by wrichtmyer on 2009-01-24
Bump. Please.

I am not quite sure if my virtualbox is 64 bit, all I did was install VB from the Add/Remove programs.

---

### Post by canabal on 2009-01-24
I wish I could help, I just put together the tutorial, but I do not know too much about the process other than following them directly.

---

### Post by sebastien_vigneau on 2009-01-27
Thank you very much for this tutorial. Everything works perfectly following it, except that I need to mount the grub.iso image in VirtualBox, and therefore don't have room to mount the guest additions at the same time.
I think one workaround could be to boot from a floppy img containing grub instead of the iso file. However, I didn't manage to create such an image working with VirtualBox. Could you please tell me if you think this is the right way to do and, if it is the case, indicate me the detailed step to create the floppy img?
Thank you for your help!

---

### Post by sebastien_vigneau on 2009-01-28
I just realized my previous question came from misunderstanding how to install the guest additions. They have to be installed inside the guest using the iso guest addition image mounted in VirtualBox, after the guest has booted (it is then safe to unmount the grub iso from VirtualBox).

However, since the guest additions mess up the original drivers in the guest, which made it impossible to log in the real Vista thereafter, I had to remove the guest additions and to restore Vista to a previous state. So, I just abandoned the idea of using my Vista partition from inside Ubuntu using Virtual Box...

---

### Post by run1206 on 2009-02-09
you got your Vista partition to work with guest additions?  :?
i ask because i virtualized my Ubuntu/XP partitions on my last laptop and didn't have to use guest additions...

plus i saw this on the XP version of the tutorials...
> **Mr. Picklesworth said:**
> Quick lesson of the day:
Do not. DO NOT install VirtualBox Guest Addins for the "guest" OS if you still plan to dual boot with it; Windows will fail on startup when booting on its own. If you (like I) do this, do not panic. Boot Windows via VirtualBox, uninstall the guest addins, restart, and then (still in VirtualBox) run System Restore. And then never do it again.


> **Mr. Picklesworth said:**
> Nope, my little lesson is directed at nobody. I just did that, then thought I should share what I learned lest anyone else bumps into it :)

That was with Windows Vista Home Premium, by the way. Results elsewhere may vary. (But don't count on it :/).
Kind of a shame, since the guest addins certainly did work. Ah well, can't have everything. It's still plain cool, regardless of how the integrity of the universe hangs by a thread whenever it is attempted.

could someone confirm this for me?  i haven't virtualized my Vista partition yet and wanna make sure everything goes ok.  thanks in advance :)


edit:just saw a few pages later that the Vista will search the CD for the base drivers :oops: :)
guess i'll try to virtualize and see what happens...

---

### Post by canabal on 2009-02-13
Mine works using the guest additions, but mileage may vary.  I think I will take it out of the tutorial if others have problems.

You do not need the guest additions in order to use vista in the VM, you can run it without.

---

### Post by run1206 on 2009-02-13
> **canabal said:**
> Mine works using the guest additions, but mileage may vary.  I think I will take it out of the tutorial if others have problems.

You do not need the guest additions in order to use vista in the VM, you can run it without.

k, do you have to reactivate Vista in either case?  i only have the key on the back of my laptop; they didn't have a CD in the package :(

---

### Post by canabal on 2009-02-13
The activation problem is a continuing saga that I have no idea what to do about.  I have actually since switched to windows 7 so I cant do much else to help.  Windows 7 is MUCH better to use in a VM.

---

### Post by Veedrac on 2009-02-19
I'm struggling to get this. I'm using Wubi to install my Ubuntu, due to network problems I'm having on my native installation. I've managed to get somewhere, but the point I need to type in ```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
``` and replace  '/dev/sda -partitions 2' with the right location.

Here's the problem. I have no clue how to do that xD. I have managed to do something, but when I tested it it goes like this:
 
 WINDOWS BOOT MANAGER
 -CHOOSE WINDOWS VISTA
 --GO BACK TO WINDOWS BOOT MANAGER
 -CHOOSE WUBI INSTALLATION
 --START TO LOAD KERNEL BUT STATES:
> This kernel requires an x84-64 CPU, but only detected an i686 CPU.
Unable to boot - please use a kernel appropriate for your CPU.

Any help? Thnx.

---

### Post by t2dcarla on 2009-03-11
I followed the instructions to use windows Vista that is on the original hard drive that came with the computer (a different drive than my ubuntu install).  When starting an instance of Vista through Virtualbox I just get a blank screen.  If I "reset" the Vista VM I get the windows "repair" screen.  If I choose to repair vista I get the message: "the boot selection failed because a required device is inaccessable."

Any ideas?  Thanks.

---

### Post by run1206 on 2009-03-11
i have not attempted to boot my existing Vista partition. Someone has to figure out the continuous activation problem. :?
I'd do it, but i don't have a recovery CD for my Vista partition yet.  

tsdcarla: check to see if you can still boot into your Vista partition (natively)

Veedrac:  check your menu.lst file to see what your partition name will be...
```
sudo gedit /boot/grub/menu.lst
```

i'm going to try to research more about the Vista instance in VM (since i finished school, more time to figure out this problem).  I'll also check the possible solution that Sand Lee was originally gonna try; see where that may lead to.

---

### Post by t2dcarla on 2009-03-12
> **run1206 said:**
> i have not attempted to boot my existing Vista partition. Someone has to figure out the continuous activation problem. :?
I'd do it, but i don't have a recovery CD for my Vista partition yet.  

tsdcarla: check to see if you can still boot into your Vista partition (natively)


run1206,

Thanks for the response.  I can still boot my Vista.  I can do this by booting through GRUB which uses the 'map' command to swap hd0 and hd1 so that Vista will boot properly or I can use the BIOS boot menu to select the Vista drive as the boot drive.

Could the 'map' commands in the GRUB menu.lst file be part of the problem?  I mean... are they not being implemented?

Here's my menu.list file:
default		0
timeout		1
title		Windows Vista/Longhorn (/dev/sdb1 hd1,0) (loader)
root		(hd1,0)
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by run1206 on 2009-03-12
Not too sure how it should look like when virtualizing the Vista partition. 
here's what i have as of today for the Vista section in menu.lst.

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (Acer Recovery partition)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (Main Partition)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

i don't think i map in mine :?

when i virtualized XP last year, i still used the same GRUB that came with Ubuntu, no mapping. ( i know how there is an option to choose which "bootloader" to use for each OS's particular bootup process, i stayed with Ubuntu's GRUB).

---

### Post by riskomt on 2009-03-12
Hello guys. I have a problem. I am new to the ubuntu and I need for work win. I have Vista installed on my pavilion dv5-1099 but when I follow the manual and start the Machine I get grub error 17. I dont know what to do. Please help


Edit: All right, I managed the grub 17 error . It was because I hadn't the grub.iso image mounted. Somehow no one mentioned it. But now. When I try to boot the Vista partition I get : error 25 : disk read error. Some clues ?

Edit 2: So the Error 25 was because I deleted ( to be sure ) the linux boot options. The error occured ,cos it expected a second boot option. But now I get the error 13 invalid or executable format. I'm getting sick of it :(

---

### Post by riskomt on 2009-03-16
Please guys, help. Im so close to get the stupid Vista working and no one can help ?

---

### Post by run1206 on 2009-03-16
are you dual-booting your partitions?

---

### Post by riskomt on 2009-03-17
Yes. Win Vista is on sda1, linux on sda5. Im in linux trying to boot sda1 in virtual box.

---

### Post by run1206 on 2009-03-17
are you using the GRUB bootloader for loading both at startup?  there's a certain way you have to make the hardware for virtualizing Vista (similar to the hardware profile when attempted in XP).  I'm not sure how to get the permissions to work in Vista, thus why i haven't virtualized my Vista partition yet.  My only suggestion is to try virtualizing very similar to how XP would be.  (i saw you posted in the "existing XP" virtualization thread as well)  try that method and see if you can make a workaround for the activations as well.

---

### Post by riskomt on 2009-03-17
> **run1206 said:**
> are you using the GRUB bootloader for loading both at startup?  there's a certain way you have to make the hardware for virtualizing Vista (similar to the hardware profile when attempted in XP).  I'm not sure how to get the permissions to work in Vista, thus why i haven't virtualized my Vista partition yet.  My only suggestion is to try virtualizing very similar to how XP would be.  (i saw you posted in the "existing XP" virtualization thread as well)  try that method and see if you can make a workaround for the activations as well.

But the problem is: when I choose my vista os from grub i get the error 13 invalid or executable format and I cant move behind it. I tried to google the error code but I found only hints about MBR and Vista original bootloader.

And how is it with the grafik in Vbox. I heard it makes trouble to run a fullscreen app or something. Thats not good. I need it to run a 3D drawing programm called Autodesk Inventor Suite 2009 and now Im afraid it wont work.

---

### Post by jjpcexpert on 2009-03-17
> **acebrain01 said:**
> So for my first post here. My vista is on it's own hard drive not on sda but sdb and i can not get grub to load it. also could only create passthru by sudo the command. any help would be greatly appreciated. Just boot from your Vista C: drive not your ubuntu sda1.

---

### Post by run1206 on 2009-03-17
riskomt:  
post up your menu.lst output
type this code into a terminal (Applications -> Accessories -> Terminal), 
```

sudo gedit /boot/grub/menu.lst

```

here is mine...
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (Acer Recovery partition)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (Main Partition)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

check if the windows section to your menu.lst is similar (savedefault,makeactive, and chainloader)

(Acer made two partitions, this is why i have a recovery partition and the main partition)

---

### Post by riskomt on 2009-03-17
> **run1206 said:**
> riskomt:  
post up your menu.lst output
type this code into a terminal (Applications -> Accessories -> Terminal), 
```

sudo gedit /boot/grub/menu.lst

```

here is mine...
```

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c6853b2c-6e0b-40b2-ba6a-92ed9b86c6d5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista (Acer Recovery partition)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (Main Partition)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

check if the windows section to your menu.lst is similar (savedefault,makeactive, and chainloader)

(Acer made two partitions, this is why i have a recovery partition and the main partition)

You didnt specify witch one you want to see. Here is my original menu.lst

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue
splashimage=(hd0,4)/boot/grub/splash.xpm.gz

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		3a5446b9-3612-4c1d-93bc-f3e4d0db1e80
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro splash
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3a5446b9-3612-4c1d-93bc-f3e4d0db1e80
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#uuid		3a5446b9-3612-4c1d-93bc-f3e4d0db1e80
#kernel		/boot/vmlinuz-2.6.27-7-generic #root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
#uuid		3a5446b9-3612-4c1d-93bc-f3e4d0db1e80
#kernel		/boot/vmlinuz-2.6.27-7-generic #root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro  single
#initrd		/boot/initrd.img-2.6.27-7-generic

#title		Ubuntu 8.10, memtest86+
#uuid		3a5446b9-3612-4c1d-93bc-f3e4d0db1e80
#kernel		/boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#chainloader	+1
```

And here is my menu.lst for the virtual machine

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3a5446b9-3612-4c1d-93bc-f3e4d0db1e80

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader	+1

title		Windows Vista
root		(hd0,1)
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#chainloader	+1

```

As you see I tried many things. Changing partition, swaping drives. But so far nothing helped. The savedefalut is in the manual written I should remove for safety of my original grub.

---

### Post by run1206 on 2009-03-17
> **riskomt said:**
> 

```


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
savedefault
chainloader	+1


[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#chainloader	+1
```
[/B]

And here is my menu.lst for the virtual machine

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader	+1

title		Windows Vista
root		(hd0,1)
chainloader	+1

[B]# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
#title		Windows Vista/Longhorn (loader)
#root		(hd0,2)
#savedefault
#chainloader	+1[/B]

```

As you see I tried many things. Changing partition, swaping drives. But so far nothing helped. The savedefalut is in the manual written I should remove for safety of my original grub.

why is your Vista partition commented out? :?
unless (hd0,2) doesn't map directly to your Windows partition....

i don't recall having 2 menu.lst files when i virtualized :?

---

### Post by riskomt on 2009-03-17
> **run1206 said:**
> why is your Vista partition commented out? :?
unless (hd0,2) doesn't map directly to your Windows partition....

i don't recall having 2 menu.lst files when i virtualized :?

Its probably because the second menu.lst is burned in the grub.iso that is mounted in the vbox cd rom. The second one is disabled because in my original grub I use the first one to boot to Vista so I expected the second one is only a partition without any system on it. Its the data partition of mine.

---

### Post by canabal on 2009-04-06
Made a couple edits and confirmed it works the same with Windows 7.

---

### Post by run1206 on 2009-04-06
> **canabal said:**
> Made a couple edits and confirmed it works the same with Windows 7.

nice :)
do you still have the reactivation problems in Windows 7, or is that cleared up in the new version?

---

### Post by canabal on 2009-04-06
So far no issues, but on vista mine did not pop up for a couple weeks.  If it does appear I will update.

Also I am running this from Jaunty and it is working fine.

---

### Post by GapToN on 2009-04-22
Hi guys this has been a great walkthrough. I followed everything and seem to stumble upon the last bit.... which is to boot Vista in VB.

The funny thing is there is no error messages whatsoever, it simply got STUCK in the Vista splash screen, the one that appears just before the desktop is being loaded and shown.

If anyone have any idea what might be the problem?

I'm guessing its related to my hardware.... but no idea what and why.

---

### Post by GapToN on 2009-04-22
I discovered that my vmdk file is not classed as Writethrough, its just Normal.

Would this be the cause? I have been searching for methods to create or modify the vmdk to make it "Writethrough" but I couldn't find anything useful.

Would be great if someone can help out a bit.

Edited:

I notice that Vista (VM) loads the vmdk hardisk for a short while, about 2 seconds, then all activities stopped. And since Vista is not able to load whatever files it needs, its just stuck at the splash screen forever.

It seems very weird to me that the disk can load everything it needs right up to the splash screen, coz I assume being able to get to the splash screen means VirtualBox already have access to the actual partition of my physical hardisk via vmdk.

---

### Post by flabbergasted on 2009-05-01
I am glad I found this tutorial. I think it is great and I am happy to see so many people are getting this to work. Hopefully I will soon join the ranks of the successful. In the mean time...

When I run the second command in step two, I am greeted with,

"Error opening the raw disk '/dev/sda': VERR_ACCESS_DENIED
The raw disk vmdk file was not created"

My vista partition is actually on /dev/sda1, but I get the same message when running that. 

"Error opening the raw disk '/dev/sda1': VERR_ACCESS_DENIED
The raw disk vmdk file was not created"

I have two 250 gig hd's with windows on the first and Ubuntu on the second. I have made the ntfs file system writable and can write to it. Any ideas what I might be lacking???

BTW, the command as I ran it was,

```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda1 -partitions 2 -relative -register
```

**UPDATE:** Oops! I seem to have skipped over "Log out and log back in here... " Now the message has changed. See below.

---

### Post by flabbergasted on 2009-05-02
OK, I have now successfully gone through the entire setup, but now when I try to start the virtual Vista I am greeted with,

"Error 15, file not found


Press any key to continue....."

What file? All of the steps 1 thru 4 went well. Step 6 is now my first hickup and I am now stuck. Any help?

---

### Post by valiantdust on 2009-05-06
I had a similar problem, but mine was an Error 21. I had forgotten to tell VBox to boot the grub.iso (Settings --> CD/DVD-ROM --> Check "Mount CD/DVD Drive" --> Check "ISO Image File" and click the little folder icon to the right --> add your grub.iso to the CD/DVD Images tab, select it and you're all set). If that's not the issue, I'd check some of your other settings, e.g. did you specify your partition(s) correctly in the VBoxManage command, etc.

That said, I still haven't been able to get my existing Vista x64 partition to boot up successfully in VBox (running Jaunty AMD64). It throws an error if VT-x/AMD-V is disabled (had to go into BIOS and turn on virtualization support too). With VT-x/AMD-V enabled, it starts to boot ... VERY slowly. VBox window just gives a big blank screen, then after a minute or two it resizes to a smaller blank screen, then VBox aborts. 

I checked the logs and found these at the end (looked good prior to these):

```
00:01:30.895 !!Assertion Failed!!
00:01:30.895 Expression: <NULL>
00:01:30.895 Location  : /build/buildd/virtualbox-ose-2.1.4-dfsg/src/recompiler_new/VBoxRecompiler.c(4346) cpu_abort
00:01:30.895 fatal error in recompiler cpu: triple fault
```

Anyone have any ideas?

---

### Post by ohnoezitasploded on 2009-05-08
Has anyone tried this for a setup where both my Vista and Ubuntu install are on a software raid 0 array?

How would I modify the command:
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
to access a the raid partition?  

Thanks!

---

### Post by ivbrajkovic on 2009-05-08
I have the same problem with the same log. 

```
00:01:30.895 !!Assertion Failed!!
00:01:30.895 Expression: <NULL>
00:01:30.895 Location  : /build/buildd/virtualbox-ose-2.1.4-dfsg/src/recompiler_new/VBoxRecompiler.c(4346) cpu_abort
00:01:30.895 fatal error in recompiler cpu: triple fault
```

I am running Jaunty x86 and I still haven't been able to get my existing Vista x64 partition to boot up successfully in VBox.

Could anyone help on this?

---

### Post by ohnoezitasploded on 2009-05-08
> **ohnoezitasploded said:**
> Has anyone tried this for a setup where both my Vista and Ubuntu install are on a software raid 0 array?

How would I modify the command:
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/sda -partitions 2 -relative -register
to access a the raid partition?  

Well, I figured this part out:

the command for raid arrays will be:
```
VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/WinHD.vmdk -rawdisk /dev/mapper/<RAID NAME> -partitions <###> -relative -register
```where:
<RAID NAME> is the name of your array, found by doing an "ls /dev/mapper/" -- it's the one without any numbers after it.

and <###> is the partition number, which may be found by running:
```
 VBoxManage internalcommands listpartitions -rawdisk /dev/mapper/<RAID NAME>
```Sorry if that's obvious to everyone else, but it wasn't to me.  Now I'm stuck at importing the existing vmdk file in VirtualBox OSE, I'm getting the cryptic error message:

 Could not open the hard disk [COLOR=#0000cc]'/home/max/.VirtualBox/WinHD.vmdk'[/COLOR].
 VD: error opening image file [COLOR=#0000cc]'/home/max/.VirtualBox/WinHD.vmdk'[/COLOR] (VERR_ACCESS_DENIED).
 
    Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  HardDisk2
   Interface: 
  IHardDisk2 {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}
   Callee: 
  IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

any thoughts on that?

---

### Post by ohnoezitasploded on 2009-05-08
> **ohnoezitasploded said:**
>  I'm getting the cryptic error message:

 Could not open the hard disk [COLOR=#0000cc]'/home/max/.VirtualBox/WinHD.vmdk'[/COLOR].
 VD: error opening image file [COLOR=#0000cc]'/home/max/.VirtualBox/WinHD.vmdk'[/COLOR] (VERR_ACCESS_DENIED).
 
    Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  HardDisk2
   Interface: 
  IHardDisk2 {ed6e2525-c2fd-42a4-917a-7a9045ac9e15}
   Callee: 
  IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

any thoughts on that?

Moving on!  It was a permissions problem, setting:
```
sudo chmod 777 /home/max/.VirtualBox/WinHD4-pt.vmdk
sudo chmod 777 /home/max/.VirtualBox/WinHD.vmdk
sudo chmod 777 /home/max/.VirtualBox/VirtualBox.xml
```

fixed the problem.  Vista booted and, of course, immediately went BSOD on me.

---

### Post by flabbergasted on 2009-05-16
I have cleared a few obstacles, and have progressed to where my vista amd64 system starts to boot in my ubuntu host. The problem I am having
now is two fold and I am not sure that one has to do with the other.

The first problem is a message from VB informing me that 

> The virtual machine window is optimized to work in 32 bit color mode but the color quality of the virtual display is currently set to
24 bit.

Please open the display properties dialog of the guest OS and select a 32 bit color mode, if it is available, for best possible performance
of the virtual video subsystem.

Note. Some operating systems, like OS/2, may actually work in 32 bit mode but report it as 24 bit (16 million colors). You may try to select
a different color quality to see if this message disappears or you can simply disable the message
now if you are sure the required color quality (32 bit) is not available in the given guest OS.

I booted into vista and it had to do a repair after the attempt to boot it as a guest. It is set for a 32 bit resolution (even though there
is no such thing, as I understand it.) and ubuntu goes no higher than 24 bit, since that is the highest it can really go anyway.

So after clicking the ok button, the windows boot manager pops up a lengthy message that states,

> Windows failed to start. A recent hardware or software change might be the problem. To fix the problem:

1. Insert your windows installation disc and restart your computer.
2. Choose your language settings and then click next.
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status 0xc000000f

Info: The boot selection failed because a required device is inaccessible.

My choices at the bottom are then "ENTER=continue" or "ESC=Exit".

Pressing Enter puts me on the next windows where I can choose to "Launch startup repair" or "Start Windows normally".

The repair option puts me back at the last screen and the "Start Windows normally" results in an abort in VB's attempt at starting the guest
machine.

I feel like I am a hairs breadth from getting this going which would then give me a perfect PC since I hate windows but need a couple of
applications for work. If anyone has any ideas, I would greatly appreciate it.

If it is any help I am on an HP DV9927cl and each operating system has its own 250 Gig hard drive. I have 4 Gb or ram of which I am
allotting 1 Gb to windows vista.

---

### Post by flabbergasted on 2009-05-18
Anybody still in here? ):P I was really hoping to get this figured out. I have been working on getting this going for over a week and I figured that some of you who have posted in this thread would have a bit of guidance. I could use it. I feel like I am wandering in the dark here in this forest.

---

### Post by noodles21 on 2009-05-21
how did you fix the GRUB error 17?

---

### Post by flabbergasted on 2009-05-22
> **noodles21 said:**
> how did you fix the GRUB error 17?

Is that the error about there not being a bootable image or partition whereever it is you are looking to boot? If it is, I got that one, too, but it was because I had a flash drive plugged into my usb port and VB was looking there first since it was setup to look there first. After I pulled out the flash drive, the problem cleared.

If you are having a similar problem, check your boot order under "Settings" and the "Advanced" tab. I unchecked the "Floppy" option since I do not have one, nor would I use one. I like to keep my options to a bare minimum. Fewer things that can go wrong.;)

---

### Post by flabbergasted on 2009-05-28
Well, it has been six days since I posted my last reply to this thread. I guess there is no resolution for the problem I am having. I will try over at the virtualbox forum again and post here if I find a resolution elsewhere.

---

### Post by jmw86069 on 2009-06-06
valiantdust, just wanted to say I have the same error as you, except that I think the line indicating the problem is higher up the log file -- curious if it is the case for you as well.
> 00:00:07.888 Guest Log: BIOS: int13_diskette: unsupported AH=41
00:00:11.747 Display::handleDisplayResize(): uScreenId = 0, pvVRAM=00007f5164036000 w=640 h=480 bpp=0 cbLine=0x140
00:00:13.436 
00:00:13.436 !!Assertion Failed!!
00:00:13.436 Expression: <NULL>
00:00:13.436 Location  : /home/vbox/vbox-2.2.4/src/recompiler_new/VBoxRecompiler.c(4274) cpu_abort
00:00:13.436 fatal error in recompiler cpu: triple fault
I suspect the line with **"Guest Log: BIOS: int13_diskette: unsupported AH=41"** is the problem. I've Googled for a couple days with no luck. It does seem like similar issues have been seen and resolved previously, though apparently those fixes are only point-fixes for that specific scenario. I'll file a bug and post a link here, but let me know if you've resolved your problem and if you have the same log entry?
I have an HP Pavilion DV7-1245 laptop, AMD Turion RM-72.

---

### Post by run1206 on 2009-06-09
> **flabbergasted said:**
> Well, it has been six days since I posted my last reply to this thread. I guess there is no resolution for the problem I am having. I will try over at the virtualbox forum again and post here if I find a resolution elsewhere.

yeah, i was re-reading all the posts her and noticed noone figured out the fixes for the activation, or the errors in grub :(

i'm gonna check the virtualbox forums as well and see what they say about it with Vista.

---

### Post by gagagoogoo on 2009-09-08
a quick question: is it possible to sorta go the opposite way...? as in, install Vista on a physical drive/partition via VBox then try and boot the partition. lot of ppl want to access existing installs but couldn't find many/any wanting to go the other way.

i'm in the install phase right now. after that a small edit in the bootloader then a reboot should do it...?

---

### Post by gagagoogoo on 2009-09-09
had another couple of quick questions...

1) as one user asked earlier, unlike in the screenshot shown in the tutorial, my hard disk is listed as "Normal" as opposed to "Writethrough". does that makeany difference?
2) i entered the command for adding user to the groups (disk and vboxusers) and checked the group file to see if it worked. was ok for "vboxusers" but couldn't find any group called "disk"?

thanks.

---

### Post by tukus on 2009-09-28
> **gagagoogoo said:**
> 

my hard disk is listed as "Normal" as opposed to "Writethrough". does that makeany difference?



I'd like to bump this.

So close with this but Vista goes into recovery mode, like the previous session crashed.

Anyone found a solution to the Normal v Writethrough issue?  Maybe that's my problem...

---

### Post by canabal on 2009-11-20
Normal should be fine.  When I made the images, I forgot to unmount the partition, so actually normal is likely better.

---

### Post by run1206 on 2009-11-20
canabal, did you ever fix the issue of repeated activations during login for Vista?   I still haven't virtualized my vista and Jaunty partitions yet.

---

### Post by canabal on 2009-11-25
No, I am using Windows 7 now, but the same thing is happening.  Thankfully it is an enterprise copy from my school, so there is no limit on the activations, but it is still annoying.

---

### Post by sanesto on 2009-12-23
what can i do if i use ubuntu 9.10. 
It's not the same for the first part (the grub one), cz ubuntu 9.10 use the grub2, so when i typed:  
mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
i got this message: 
cp: cannot stat `/usr/lib/grub/*-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory

so do you have any idea plz to solve my problem.

Thx in advance!

---

### Post by C4Rd0 on 2010-01-05
> **sanesto said:**
> what can i do if i use ubuntu 9.10. 
It's not the same for the first part (the grub one), cz ubuntu 9.10 use the grub2, so when i typed:  
mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
i got this message: 
cp: cannot stat `/usr/lib/grub/*-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory

so do you have any idea plz to solve my problem.

Thx in advance!
I have the same problem with grub. Any idea?

---

### Post by werecatomega on 2010-01-07
it's because grub doesn't use menu.lst anymore. any solutions?

---

### Post by C4Rd0 on 2010-01-08
Does exists another way to create a grub boot iso, with the possibility to change grub menu items (to force loading only windows partition) ?

EDIT: another possible way is to install mrb packet. Using command install-mbr, it's possible create an "ad-hoc" .mbr file which will included into virtual image disk creation, using the option -mbr.
```

install-mbr realVista.mbr -f -p 4

VBoxManage internalcommands createrawvmdk -filename ~/.VirtualBox/RealVista64HD.vmdk -rawdisk /dev/sda -partitions 4 -mbr realVista.mbr -relative -register

```In this example the mbr file named realVista.mbr, created forcing partition to boot 4 partition, is included into RealVista64HD.vmdk with option *-mbr realVista.mbr*

---

### Post by Raditude on 2010-01-10
> **sanesto said:**
> what can i do if i use ubuntu 9.10. 
It's not the same for the first part (the grub one), cz ubuntu 9.10 use the grub2, so when i typed:  
mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
i got this message: 
cp: cannot stat `/usr/lib/grub/*-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory

so do you have any idea plz to solve my problem.

Thx in advance!

I've ran into the same problem. Any solutions?

---

### Post by master620 on 2010-01-19
i'm having problems with the very first line... this is exactly what i entered into the terminal, and what i got back in response...

thefox@ubuntu:~$ mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
cp: cannot stat `/usr/lib/grub/*-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
thefox@ubuntu:~$ 

any idea on what i am supposed to do? i'm using karmic (9.10) but the begining of the thread says its for 9.04, though throughout my use of karmic i have yet to have any problems doing things that were done on 9.04... i dont feel like formatting my win7 partition just so i can reinstall it with a virtual machine... mainly because it has my games on it and MW2 doesn't have any way for you to backup the game files.. i'm not saying i want the virtualbox to be able to play games, just want to be able to use it when i need it without having to reboot every time, if i want to play a game then i'l just reboot, since it isn't like you can do anything except that game while its running anyway lol.

---

### Post by bbqsauced on 2010-01-28
I'm interested in knowing this as well.

---

### Post by Jackzor on 2010-01-28
> **master620 said:**
> i'm having problems with the very first line... this is exactly what i entered into the terminal, and what i got back in response...

thefox@ubuntu:~$ mkdir -p iso/boot/grub ; cp /usr/lib/grub/*-pc/stage2_eltorito /boot/grub/menu.lst iso/boot/grub
cp: cannot stat `/usr/lib/grub/*-pc/stage2_eltorito': No such file or directory
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
thefox@ubuntu:~$ 

any idea on what i am supposed to do? i'm using karmic (9.10) but the begining of the thread says its for 9.04, though throughout my use of karmic i have yet to have any problems doing things that were done on 9.04... i dont feel like formatting my win7 partition just so i can reinstall it with a virtual machine... mainly because it has my games on it and MW2 doesn't have any way for you to backup the game files.. i'm not saying i want the virtualbox to be able to play games, just want to be able to use it when i need it without having to reboot every time, if i want to play a game then i'l just reboot, since it isn't like you can do anything except that game while its running anyway lol.

Karmic uses Grub2 Not Grub1. Thats why thats not working.

---

### Post by muffinboy on 2010-02-16
sorry for thread necromance, but i followed the directions, and when vista goes to boot it gives me the "windows did not shut down properly".

If i try to start normally, it hangs at a black screen, if i boot safe mode, it hangs at crcdisk.sys.


any suggestions?

---

### Post by cyrusthegreat on 2010-03-14
Rise!

This post concerns the "fatal error in recompiler cpu: triple fault" error some have posted about in this thread.  I'm experiencing the same error along with a Guru Meditation when I try to boot my native Win 7 Ultimate partition in VirtualBox when VT-x/AMD-V are enabled.  If I disabled hardware virtuatlization, the VM boots fine.  My processor supports this feature and works perfectly fine with non-native OSes I use on this computer.  Has anyone been able to resolve this issue?

Regards.

---

### Post by tilixibr on 2010-03-24
My /usr/lib/grub folder doesn't have a stage2-eltorito file. Help?

---

### Post by Azazel on 2010-04-12
This how-to does not work with grub2. grub2 doesnt have a stage2-eltorito file.

It is possible to revert from grub(1.97~beta4) to grub(0.97) to be compatible with this post, but this seems counter productive.

To learn about Grub2 and also how to revert to legacy grub go here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Section 12 discusses reverting

For everyone else who does not want to revert (such as myself) we need a real solution rather than a workaround. I've been working with making an iso file of Grub2 and editing /boot/grub/grub.cfg but I haven't got a working configuration yet.

I keep getting errors such as "no kernel" and "cannot get C/H/S values" after trying to boot from a Grub2 entry.

I'm not exactly sure how the drive device naming works inside the virtual machine.

Any advice?

---

### Post by hgurol on 2010-05-14
Hey Azazel,

Did you manage to have any progress with this?

Thanks...


> **Azazel said:**
> This how-to does not work with grub2. grub2 doesnt have a stage2-eltorito file.

It is possible to revert from grub(1.97~beta4) to grub(0.97) to be compatible with this post, but this seems counter productive.

To learn about Grub2 and also how to revert to legacy grub go here: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Section 12 discusses reverting

For everyone else who does not want to revert (such as myself) we need a real solution rather than a workaround. I've been working with making an iso file of Grub2 and editing /boot/grub/grub.cfg but I haven't got a working configuration yet.

I keep getting errors such as "no kernel" and "cannot get C/H/S values" after trying to boot from a Grub2 entry.

I'm not exactly sure how the drive device naming works inside the virtual machine.

Any advice?

---

### Post by hgurol on 2010-05-17
You lazy Azazel, where did you get lost :)

Take a look at my post over here. I believe it will make you happy...

[http://ubuntuforums.org/showpost.php?p=9313579&postcount=472](http://ubuntuforums.org/showpost.php?p=9313579&postcount=472)

---

### Post by travisc94 on 2010-07-22
Here is a fix to this, which works for me.

Running Ubuntu 10.04 and Virtualbox

[http://www.in-the-attic.co.uk/2010/06/05/booting-windows-7-from-an-existing-partition-inside-ubuntu-virtual-box/]("http://www.in-the-attic.co.uk/2010/06/05/booting-windows-7-from-an-existing-partition-inside-ubuntu-virtual-box/")

---

### Post by raivo on 2010-08-25
Has anyone got it working with SATA drives?

---

### Post by asndo on 2010-08-27
> **run1206 said:**
> canabal, did you ever fix the issue of repeated activations during login for Vista?   I still haven't virtualized my vista and Jaunty partitions yet.

 Hi,  I would like also to take advantage of booting win7 both through a dual boot and virtual box. I was wondering on the problem of these activations and an idea came upon me: wouldn't it be better to install them independently and then rsync the appropriate files regularly so that just one installation of a given software would be sufficient? 
 Does someone know which folders apart from Program Files and Users in Win should be synchronized? Or rather which shouldn't because they contain hardware-specific files that would raise conflict between the systems?

---

### Post by newboyo on 2010-09-28
Flabbergasted wrote -

 	Quote:
 	 	 		 			 				Windows failed to start. A recent hardware or software change might be the problem. To fix the problem:

1. Insert your windows installation disc and restart your computer.
2. Choose your language settings and then click next.
3. Click "Repair your computer."

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

Status 0xc000000f

Info: The boot selection failed because a required device is inaccessible. 			 		 	 	 
My choices at the bottom are then "ENTER=continue" or "ESC=Exit".



I too am stuck at the same point. could someone please help.

Rgds

New

---

### Post by XGaSt on 2010-10-29
About activation issue, try to use WAT Remover in windows 7 with natively boot

---

### Post by parminides on 2010-12-14
There's a lot of chatter in this thread about it not being valid for grub2. However, I found some tutorials that seem to get around that problem.

I'm trying the method of [http://forums.virtualbox.org/viewtopic.php?f=7&t=8458&start=0](http://forums.virtualbox.org/viewtopic.php?f=7&t=8458&start=0), which is more involved.

In step 4, I was able to run FixMbr in recovery mode, which wiped out grub as expected.

After that it says to

```

dd if=/dev/sda of=location/file.mbr bs=512 count=1

```

I don't see where the mbr that FixMbr created is indicated. The "if" part of the command is supposed to be the input file and "of" is supposed to be the output file. There's no input mbr "file" or location specified. The "input" file seems to be the entire disk. How does dd know to "Get the MBR to file" from the above command?

Of course, all these questions would be academic and I'd gladly continue to live in ignorance if I had actually been able to get it to work. So I'd appreciate some education.

---

### Post by Syed75 on 2011-02-22
Err2Err3

I can't find a resolution..  :confused::confused::confused:

---

### Post by safira218 on 2011-02-23
> **canabal said:**
> Updated to add GRUB boot CD.
Can somebody please confirm that once I set this up I won't have to  continually re-activate Vista each time I boot it either natively or  virtually? I intend to be able to boot it alternately virtually and  natively continuously forever. Does that make sense? Does it somehow  retain the previous hardware profile or how does that work since I keep  reading Vista doesn't allow for multiple hardware profiles...?

---

### Post by hiKen on 2011-04-18
anyone tried booting a Windows 7 partition from Maverick Merkaat?


cumps

---

### Post by peepingtom on 2011-05-01
> **parminides said:**
> There's a lot of chatter in this thread about it not being valid for grub2. However, I found some tutorials that seem to get around that problem.

I'm trying the method of [http://forums.virtualbox.org/viewtopic.php?f=7&t=8458&start=0](http://forums.virtualbox.org/viewtopic.php?f=7&t=8458&start=0), which is more involved.

In step 4, I was able to run FixMbr in recovery mode, which wiped out grub as expected.

After that it says to

```

dd if=/dev/sda of=location/file.mbr bs=512 count=1

```

I don't see where the mbr that FixMbr created is indicated. The "if" part of the command is supposed to be the input file and "of" is supposed to be the output file. There's no input mbr "file" or location specified. The "input" file seems to be the entire disk. How does dd know to "Get the MBR to file" from the above command?

Of course, all these questions would be academic and I'd gladly continue to live in ignorance if I had actually been able to get it to work. So I'd appreciate some education.

It's copying the first 512 bytes of /dev/sda . The MBR is stored in the first 512 bytes of a drive.

I find it surprising that pretty much no guides included udev rules to give ownership of the windows parition to the vboxusers group rather than the disk group, that's probably a safeish way to fix permissions issues. I have one that works but i'm not certain I've done it properly, so i'll post it here once I know for sure.

Also, thing about always needing to "repair" Windows after alternating betwen virtual and native: I think the only way to fix it is to make a vmdk that gives access to the whole drive and adding users to the disk group, both of which are horrible ideas. It's a design flaw in Windows.

---

### Post by Nohajc on 2011-07-22
**About the activation problem:**
I believe there is a solution and it shouldn't be too difficult to get working.
It's not a question of some miraculous hacking, you just need to know which files are used for storing the activation information. With that knowledge you can perform two activations (on physical and vitrual machine) while keeping both versions of the generated files and then write a startup script to switch between them according to the environment.

I haven't written any detailed "how to" since I'm not dealing with this problem myself, but there is already one for Win XP which could be certainly modified to work with Win Vista/7.

**Useful links:**
XP Guide:
[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/](http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/)

Info about activation files:
[http://www.mydigitallife.info/how-to-backup-and-restore-windows-7-and-server-2008-r2-activation-status-activate-offline-on-reinstall/](http://www.mydigitallife.info/how-to-backup-and-restore-windows-7-and-server-2008-r2-activation-status-activate-offline-on-reinstall/)

---

### Post by pcworld on 2012-11-17
So... Did anyone get this working properly with grub2?

Edit: Works perfectly now. I suggest you this guide: [Using Virtualbox with an Existing Windows Partition]("http://geekery.amhill.net/2010/01/27/virtualbox-with-existing-windows-partition/")
If you speak German or have no problem with Google Translator English, you should really read this:
On the German ubuntuusers.de wiki there's a [very comprehensive article]("http://wiki.ubuntuusers.de/Dualboot-Windows_virtualisieren") [[translated]("http://translate.google.de/translate?hl=en&sl=auto&tl=en&u=http%3A%2F%2Fwiki.ubuntuusers.de%2FDualboot-Windows_virtualisieren")] about it which includes many troubleshooting tips.

---

### Post by wildmanne39 on 2012-11-19
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

