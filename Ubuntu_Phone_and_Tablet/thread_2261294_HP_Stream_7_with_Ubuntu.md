---
title: "HP Stream 7 with Ubuntu?"
date: 2015-01-17
forum: Ubuntu Phone and Tablet
---

### Post by Bhavin_Prajapati on 2015-01-17
*Just a disclaimer, I am very new to Linux/Ubuntu so I am learning as I go. So far the experience has been incredibly positive. *

I got a HP Stream 7 for Christmas. Seems like a lot of people picked one up/received one because it was only $100. It's a great tablet and I wonder if anyone owns this tablet and whether they tried a linux distro on it. Here are the specs

[HP Stream 7]("http://www.microsoftstore.com/store/msusa/en_US/pdp/HP-Stream-7-Signature-Edition-Tablet/productID.308781500"):
-Accessible EFI 
-Intel Atom Z3735G quad core 1.33 GHz with Burst Technology up to 1.83 GHz
-Windows 8.1 32 bit 
-32 GB SSD
-7" IPS display 
-1 GB Ram 

I just bought a OTG adapter from ebay so I can use a standard usb flash drive  so it is arriving in the next few weeks. I haven't really found anyone who has tried to run any distro on it. I think once Ubuntu Touch is released, it might be an interest tablet to try it on.

---

### Post by grahammechanical on 2015-01-17
What makes you think that this machine has an accessible UEFI? There have been reports of manufacturers modifying UEFI to only boot Windows. I think HP is one of those companies. There is a work around but do not expect it to be easy.

I am also a bit suspicious of it having 32 bit Windows 8. That could mean that the chip that holds the UEFI is also 32 bit. And that is another complication.

Regards.

---

### Post by Bhavin_Prajapati on 2015-01-17
> **grahammechanical said:**
> What makes you think that this machine has an accessible UEFI? There have been reports of manufacturers modifying UEFI to only boot Windows. I think HP is one of those companies. There is a work around but do not expect it to be easy.

I am also a bit suspicious of it having 32 bit Windows 8. That could mean that the chip that holds the UEFI is also 32 bit. And that is another complication.

Regards.

Hey there! 

[Here is a screenshot of the Stream 7 that I just took, check it out!]("http://imgur.com/XCRHwDH") I was able to access the bios and boot manager. If you visited the link I provided in the OP, Microsoft lists the Stream 7 with 32 bit Windows 8.1 and I can further verify that on the system screen. 

Hope that clears some of your questions up

I found this one on of the Amazon comments... 

The Stream 7 is a great value and its Intel architecture allows running common Linux distributions.

I installed Ubuntu Mate 14.10 32-bit on the Stream 7 and it is running well. Some things are not yet working such as the built-in Wifi (I am using a USB Wifi adaptor) and the touchscreen, (I am using an external mouse and a on-screen keyboard). I will attempt to install drivers and update the review. It seems pretty usable in its current state. As you probably know, an OTG adaptor and USB hub are required to do this. Press the power button and then volume down to enter the UEFI Startup Menu, the Secure Boot option needs to be disabled.

The Stream 7 has a 32-bit UEFI but most Linux distros only support 64-bit UEFI's so the below tweaks are required to create a live USB drive to boot from. It involves getting an install image called Fedlet that already has a 32-bit EFI directory and copying it to an Ubuntu USB and tweaking the grub.cfg file:

Download the latest Fedlet ISO file from [...] and burn it to a USB drive, (or just extract the EFI directory).
Download the Ubuntu ISO file and burn it to a USB drive (I used a 32-bit image but 64-bit images can boot with this method as well although the file layout is slightly different, the 32-bit method is described below):

- Copy the Fedlet EFI directory to the root of the Ubuntu USB drive.
- Rename the Ubuntu USB /EFI/BOOT/grub.cfg file "grub.cfg_FEDLET" (or just delete it).
- Copy the Ubuntu USB /boot/grub/loopback.cfg file to /EFI/BOOT, and rename it "grub.cfg".
- Edit the new /EFI/BOOT/grub.cfg file like below, changing each "linux" and "initrd" label to "linuxefi" and "initrdefi":

Change this:

menuentry "Try Ubuntu MATE without installing" {
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu-mate.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
initrd /casper/initrd.lz

To this:

menuentry "Try Ubuntu MATE without installing" {
linuxefi /casper/vmlinuz file=/cdrom/preseed/ubuntu-mate.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
initrdefi /casper/initrd.lz

The Ubuntu USB should now boot on the Stream 7. As you probably know, you can boot the live USB and try it out without installing it. I was able to install Ubuntu to the Stream 7's disk (eMMC drive) with no additional tweaking, it seemed to install both 64-bit and 32-bit EFI's allowing me to toggle the 32-bit EFI to boot successfully. I wiped the entire disk clean first using Ubuntu's GParted. I first made recovery media in Windows using the Recovery Manager utility and a 8 GB USB drive in case I want to restore the tablet back to factory configuration. I am also planning a dual boot install with Windows.

You can also run the Fedlet image, the touchscreen works but it ran slowly and seemed unstable on the Stream 7 so I went with Ubuntu which seems stable, runs as fast as Windows 8.1 and uses less memory.

Hope this helps.

UPDATE January 7, 2015:

The Wifi and touchscreen are working on Ubuntu 14.10 now, here are the command line installation steps I used:

Wifi (a working internet connection is required for the first two steps below, I used a USB Wifi Adapter):

sudo apt-get install build-essential linux-headers-generic git
git clone [https://github.com/hadess/rtl8723as.git](https://github.com/hadess/rtl8723as.git)

Stop at this point and fix the device ID in the below source file to match the Stream:
Edit the /YOUR HOME DIRECTORY/rtl8723as/os_dep/sdio_intf.c file, change 0xB723 to 0x0523.

cd rtl8723as
make
sudo make install
sudo depmod -a
sudo modprobe r8723bs

Touchscreen:

sudo apt-get install build-essential linux-headers-generic git (skip this if you have already done it above)
git clone [https://github.com/hadess/gt9xx.git](https://github.com/hadess/gt9xx.git)
cd gt9xx
make
sudo make install
sudo depmod -a
sudo modprobe goodix_backport

The touchscreen is currently only working in normal portrait mode, if I rotate the screen 90 degrees right or left in landscape mode, the cursor will not point where my finger is, I will look into a fix for this.

I have Ubuntu installed to the drive along with the Windows 10 Technical Preview as a dual boot. I have instructions for doing that in my review of the Stream 11 laptop which is similar since they both have the same eMMC drive: [http://www.amazon.com/review/R28HR668I6LU8Y/ref=cm_cr_pr_cmt?ie=UTF8&ASIN=B00NSHLUBU](http://www.amazon.com/review/R28HR668I6LU8Y/ref=cm_cr_pr_cmt?ie=UTF8&ASIN=B00NSHLUBU)

After Ubuntu is installed on the Stream 7, you may need to press F9 during boot up and select Ubuntu from the UEFI menu to get to the Grub Boot Menu. If the boot hangs, select "Advanced Options for Ubuntu" and select recovery mode and it should fix it.

UPDATE January 14, 2015:

Michael (below) found the solution to the touchscreen problem where the touch input does not align with the display after rotating the screen. Here are the commands to rotate it left:

xrandr -o left
xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1

Here is rotating it right:

xrandr -o right
xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 1 0 -1 0 1 0 0 1

More information is here: [http://askubuntu.com/questions/405628/touchscreen-input-doesnt-rotate-lenovo-yoga-13-yoga-2-pro/405643#405643](http://askubuntu.com/questions/405628/touchscreen-input-doesnt-rotate-lenovo-yoga-13-yoga-2-pro/405643#405643)

[http://www.amazon.com/HP-Stream-Windows-Includes-Personal/product-reviews/B00NSHLVD2](http://www.amazon.com/HP-Stream-Windows-Includes-Personal/product-reviews/B00NSHLVD2) I got it from here

---

### Post by fabian_otto_de on 2015-01-31
**Problems with the above instructions**

You said someone posted these instructions on amazon. 
I don't doubt that they may have worked for him but he has either been exceptionally lucky or has clearly withheld crucial information.

Used Distribution(s): Ubuntu 14.10(32/64bit) (Same result for both versions), Linux Mint MATE (32bit) (same result.)
I for my part haven't managed to get beyond the initrd stage in booting from a FAT32 formatted USB3 Stick. And even that only after adding the *noapic* parameter to circumvent a (repeating) bug with the IRQ-interrupts. ([ATTACH=CONFIG]259624[/ATTACH])

After manually (re-)mounting my USB Stick and the squashfs FILESYST.SQU file from the initrd ash-console I get stuck either in a kernel panic or at the login prompt which doesn't let me login because it can't verify the login credentials (user: ubuntu password:[empty]) which in turn is because the responsible scripts in in the rcS.d seem to be incapable of mounting the required temporary mount-points and copy the corresponding files to them.

KNOPPIX btw. has booted without problem.

List of errors:
[ATTACH=CONFIG]259621[/ATTACH][ATTACH=CONFIG]259622[/ATTACH][ATTACH=CONFIG]259623[/ATTACH]


Pages from which I took advice with this:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://www.kernel.org/doc/Documentation/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/kernel-parameters.txt)
[http://blog.eracks.com/2008/10/ubuntu-livecd-wont-boot-no-problem/](http://blog.eracks.com/2008/10/ubuntu-livecd-wont-boot-no-problem/)


Question:
So. What should I do?
Should I try installing Ubuntu from within Windows on a microSDCard and try booting the OS directly or should I add a specific kernel parameter?

Conclusion:
Linux on HP Stream 7 is not as easy as the guide above make it out to be.

Addendum: I haven't 'burned' the Image to the USB Stick but rather just copied it's contents but this shouldn't have any affect since I'm using grub here and not isolinux.

---

### Post by a0a0-email on 2015-02-08
Can someone make a video of hp stream 7 with ubuntu? I'm a little curious

---

### Post by Jesse_Hofseth on 2015-02-08
Note: USB installer EFI directory [I][B]attached
[/B][/I]--use Unetbootin [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) as described below--delete .zip in filename to make filename: EFI.7z
--decompress with 7-zip  [http://www.7-zip.org/](http://www.7-zip.org/) 
--copy decompressed EFI folder to root of USB install thumbdrive (use Unetbootin *before *copying EFI folder)
--attached EFI file means you do NOT have to download the Fedlet .iso!  :-)

***you will not have to compile touchscreen driver if you manually install 3.19.0 kernel after Vivid Mate install; wi-fi driver must still be compiled (links below)***

I successfully installed 32bit (later switched to 64bit for compiling Android kernel purpose) Ubuntu Mate 15.04 via the above/below-pasted Amazon tutorial. 
[LIST]
[*]First, use Windows computer management disk management to resize C: to allow room for root partition install of Ubuntu Mate 32bit 15.04; the earlier, the better, because you'll have used less disk space and Windows will let you resize more, freeing up more space for Ubuntu's ext4 root partition.
[*]Download 32bit Ubuntu Vivid Mate .iso.  The only portion of the Fedlet .iso utilized is the EFI directory. * (Skip Fedlet.iso download by using attached EFI folder)*
[*] Copy the Ubuntu Mate .iso file to the root directory of fat32 USB, then run unetbootin directing it to utilize the Ubuntu Mate .iso file you just saved to the USB.
[*] After unetbootin finishes, copy the Fedlet attached decompressed EFI folder to the USB's root directory **(skip config change if you use attached EFI folder)**.
[*]Disable secureboot in bios.  Change boot order to USB first, but you may have to power+vol down boot option choose EFI file; you will have to do the latter after install for sure.
[*] You will not have wifi or touchscreen until you follow the above/below-pasted Amazon tutorial's driver compile instructions--neither before nor after install.  Keep source folders for drivers and 'make clean' before re-compiling for future kernels.
[*] Install **grub-efi-ia32 and grub-efi-ia32-bin** before install (i.e., download Vivid packages elsewhere, if necessary).
[*]If you have a wi-fi usb adapter that ubuntu recognizes you're lucky.  I used Sgit git client on my Android phone to download the two driver source folders and I ran apt-get in Vivid Mate live-usb mate-terminal to see what packages/dependencies I needed along with: **build-essential git linux-headers-generic grub-efi-ia32 grub-efi-ia32-bin**.  I hand-downloaded the terminal printout via different computer web-browser at: [https://launchpad.net/ubuntu/vivid/i386/](https://launchpad.net/ubuntu/vivid/i386/) just appending the individual package names after the last /.  There are easier methods.  I then copied those downloaded files and git folders to live-usb and to post-install Vivid Mate to install/compile.  To install all 32bit packages in a single folder, just cd to it and: sudo dpkg -i --force-all *.deb  The compile instructions are in the above/below-pasted Amazon tutorial.  If you have to install grub through chroot after installing grub-efi-ia32 and grub-efi-ia32-bin, the command is: sudo grub-install --target=i386-efi /dev/mmcblk0p1
[*]In installer advanced manual partitioning menu, _**select install grub to the ~260mb EFI Windows boot partition.  Do not format EFI partition or modify it at all--except to select it for grub bootloader installation.  Do not create a boot partition for Ubuntu.  All you need to do is create one large ext4 root / partition in the space you created by resizing Windows in Windows (f2fs is faster on SSD than ext4, but it's not yet an Ubuntu install option).  Do not create a swap partition, because swap is bad for SSD.  Do not delete Windows recovery partition, because Windows will not boot and you'll be forced to re-install.  I made the mistake of deleting Windows recovery partition to save ~5GB and had to re-install Windows 8.1 update; that's a pain-in-the-butt but it saved 5GB.**_
[*]After installing Ubuntu Mate 32bit 15.04, install Paragon ExtFS in Windows 8.1 to enable read/write support for ext4 for Windows 8.1: [http://www.paragon-drivers.com/extfs-windows/](http://www.paragon-drivers.com/extfs-windows/)
[*]**If desired, (after successfully installing 32bit Ubuntu Mate Vivid) Ubuntu Vivid kernel 3.19.0 has better Baytrail support and is manually downloadable (then manually installed) from Ubuntu Mainline Kernel PPA**: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) just install the 32bit version of the kernel, then all headers, then 32bit headers.  This kernel always boots with battery indicator (%charge works, time estimate is way off), and the tablet actually charges if you boot normally with the charger plugged-in.  Sometimes this kernel only boots via recovery entry in Grub, and USB OTG keyboard is necessary to menu select, etc.; if you boot with USB OTG, the tablet won't charge before or after switching to plugin charger--you have to boot normally with adapter plugged in for charge to work.  Also in 3.19.0, the touchscreen is supported, so manually compiling it is unnecessary.
[/LIST]
About 32bit Ubuntu Mate 15.04 on HP Stream 7:
Compiz Fusion works!!!  Mate-tweak in Vivid Mate lets you toggle, but you might have to try a few times before Compiz choice sticks.
You'll have to recompile wifi/touchscreen drivers after install following above/below-pasted Amazon tutorial instructions and after future kernel installs (keep driver source folders and 'make clean').
Locks up sometimes, less with Marco WM desktop effects.
Touchscreen is more responsive than in Windows 8.1, so multiple keypresses register accidentally with onboard or matchbox.
I have not yet found a driver enabling battery status or USB charge.
USB OTG works like a charm, but you have to power down or boot into Windows 8.1 to charge.
Definitely worth installing, but you will soon run out of Windows 8.1 C: drive storage and have to start MKLINK files/folders to microSD, etc.
Good luck!  :-)
[https://ubuntu-mate.org/vivid/](https://ubuntu-mate.org/vivid/) choose x86 due to low RAM
[https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/comment-page-1/](https://www.happyassassin.net/fedlet-a-fedora-remix-for-bay-trail-tablets/comment-page-1/) you will only need to extract the EFI folder from the latest Fedlet .iso after download (skip this by using attached EFI folder)

_***re-pasted Amazon tutorial:***_
Why run Linux on a tablet? Because you can. Here's how
Kyle on November 29, 2014
Size Name: 7-Inch
The Stream 7 is a great value and its Intel architecture allows running common Linux distributions.


I installed Ubuntu Mate 14.10 32-bit on the Stream 7 and it is running well. Some things are not yet working such as the built-in Wifi (I am using a USB Wifi adaptor) and the touchscreen, (I am using an external mouse and a on-screen keyboard). I will attempt to install drivers and update the review. It seems pretty usable in its current state. As you probably know, an OTG adaptor and USB hub are required to do this. Press the power button and then volume down to enter the UEFI Startup Menu, the Secure Boot option needs to be disabled.


The Stream 7 has a 32-bit UEFI but most Linux distros only support 64-bit UEFI's so the below tweaks are required to create a live USB drive to boot from. It involves getting an install image called Fedlet that already has a 32-bit EFI directory and copying it to an Ubuntu USB and tweaking the grub.cfg file:


Download the latest Fedlet ISO file from [...] and burn it to a USB drive, (or just extract the EFI directory).
Download the Ubuntu ISO file and burn it to a USB drive (I used a 32-bit image but 64-bit images can boot with this method as well although the file layout is slightly different, the 32-bit method is described below):


- Copy the Fedlet EFI directory to the root of the Ubuntu USB drive.
- Rename the Ubuntu USB /EFI/BOOT/grub.cfg file "grub.cfg_FEDLET" (or just delete it).
- Copy the Ubuntu USB /boot/grub/loopback.cfg file to /EFI/BOOT, and rename it "grub.cfg".
- Edit the new /EFI/BOOT/grub.cfg file like below, changing each "linux" and "initrd" label to "linuxefi" and "initrdefi":


Change this:


menuentry "Try Ubuntu MATE without installing" {
linux /casper/vmlinuz file=/cdrom/preseed/ubuntu-mate.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
initrd /casper/initrd.lz


To this:


menuentry "Try Ubuntu MATE without installing" {
linuxefi /casper/vmlinuz file=/cdrom/preseed/ubuntu-mate.seed boot=casper iso-scan/filename=${iso_path} quiet splash --
initrdefi /casper/initrd.lz


The Ubuntu USB should now boot on the Stream 7. As you probably know, you can boot the live USB and try it out without installing it. I was able to install Ubuntu to the Stream 7's disk (eMMC drive) with no additional tweaking, it seemed to install both 64-bit and 32-bit EFI's allowing me to toggle the 32-bit EFI to boot successfully. I wiped the entire disk clean first using Ubuntu's GParted. I first made recovery media in Windows using the Recovery Manager utility and a 8 GB USB drive in case I want to restore the tablet back to factory configuration. I am also planning a dual boot install with Windows.


You can also run the Fedlet image, the touchscreen works but it ran slowly and seemed unstable on the Stream 7 so I went with Ubuntu which seems stable, runs as fast as Windows 8.1 and uses less memory.


Hope this helps.


UPDATE January 7, 2015:


The Wifi and touchscreen are working on Ubuntu 14.10 now, here are the command line installation steps I used:


Wifi (a working internet connection is required for the first two steps below, I used a USB Wifi Adapter):


sudo apt-get install build-essential linux-headers-generic git
git clone [https://github.com/hadess/rtl8723as.git](https://github.com/hadess/rtl8723as.git)
cd rtl8723as
make
sudo make install
sudo depmod -a
sudo modprobe r8723bs


Touchscreen:


sudo apt-get install build-essential linux-headers-generic git (skip this if you have already done it above)
git clone [https://github.com/hadess/gt9xx.git](https://github.com/hadess/gt9xx.git)
cd gt9xx
make
sudo make install
sudo depmod -a
sudo modprobe goodix_backport


The touchscreen is currently only working in normal portrait mode, if I rotate the screen 90 degrees right or left in landscape mode, the cursor will not point where my finger is, I will look into a fix for this.


I have Ubuntu installed to the drive along with the Windows 10 Technical Preview as a dual boot. I have instructions for doing that in my review of the Stream 11 laptop which is similar since they both have the same eMMC drive: [http://www.amazon.com/review/R28HR668I6LU8Y/ref=cm_cr_pr_cmt?ie=UTF8&ASIN=B00NSHLUBU](http://www.amazon.com/review/R28HR668I6LU8Y/ref=cm_cr_pr_cmt?ie=UTF8&ASIN=B00NSHLUBU)


After Ubuntu is installed on the Stream 7, you may need to press F9 during boot up and select Ubuntu from the UEFI menu to get to the Grub Boot Menu. If the boot hangs, select "Advanced Options for Ubuntu" and select recovery mode and it should fix it.


UPDATE January 14, 2015:


Michael (below) found the solution to the touchscreen problem where the touch input does not align with the display after rotating the screen. Here are the commands to rotate it left:


xrandr -o left
xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 -1 1 1 0 0 0 0 1


Here is rotating it right:


xrandr -o right
xinput set-prop 'Goodix Capacitive TouchScreen' 'Coordinate Transformation Matrix' 0 1 0 -1 0 1 0 0 1


More information is here: [http://askubuntu.com/questions/405628/touchscreen-input-doesnt-rotate-lenovo-yoga-13-yoga-2-pro/405643#405643](http://askubuntu.com/questions/405628/touchscreen-input-doesnt-rotate-lenovo-yoga-13-yoga-2-pro/405643#405643)

---

### Post by huwwevans on 2015-02-10
This looks great.  In fact I am thinking of getting one of these and not using windows at all.  One question though.  Is it possible to make a shell script to automate the compiling procedure for the touchscreen and wifi and then set it to run every time the kernel is updated?  This would make the tablet much more usable than if I needed a mouse every time I wanted to update the OS.

---

### Post by Jesse_Hofseth on 2015-02-11
My suggestion is keep Windows 8.1.  Linux baytrail support is incomplete so far.  For example, I just upgraded to kernel 3.19.0 (by hand-downloading from Ubuntu mainline kernel PPA) and it's finally detecting a battery!  Wi-fi and touchscreen are OK in Ubuntu Mate 15.04 32bit, as is performance/snappiness, but Windows is way, way more usable on this tablet right now.  Dual boot is definitely doable and eventually Linux will support the newer hardware enough to make it feasible as the sole HP Stream 7 OS.  Good luck!  :-)

---

### Post by litemint on 2015-02-26
Has anyone tried elementaryOs luna or freya?

Hows the battery performance running ubuntu?

---

### Post by Jesse_Hofseth on 2015-02-27
haven't tried elementaryOS, but consider the kernel version as you need one of the most recent kernels to support a Baytrail tablet.  Freya is still beta and it uses the same kernel Ubuntu Trusty used:3.13.  I recommend Ubuntu Mate Vivid due to low ram and it's closer to current linux kernel.  If you install 3.19 kernel on top of Vivid Mate you get battery recognition, charging if booted with AC adapter and touchscreen works, but you still gotta compile wifi driver as detailed above.  Trust me, you want a recent kernel with a Baytrail tablet!  Good luck!  :-)

I replaced my 32bit Vivid Mate with 64bit and it works just as well on the HP Stream 7.  I didn't want to switch but needed to to compile Android KitKat kernel.  64bit uses more RAM but it's still just as snappy.  Obviously, 32bit is better due to 1GB RAM--unless you need 64bit for some reason, like I did.

fabian, just use my tutorial on 1st page :-)

---

### Post by litemint on 2015-03-01
thanks for the input jesse, I tried the latest vivid mate 15.04 & lubuntu 15.04, I cant see my mouse cursor on the desktop, finding it difficult to click the items that you cant even know where is the cursor. (good thing though if you mouse over to an icon it will glow but still hard to navigate)

I tried lubuntu 14.10,  tried the touchscreen function stated on the 1stpage and it works even im just booting on the live usb as im typing this reply, below screen shot, Im just trying out this lubuntu on this device, I just need to backup my windows os just in case i would mess up with this tablet.

---

### Post by Jesse_Hofseth on 2015-03-03
the original installed kernel for vivid mate is goofy with respect to mouse cursor, but it eventually appears after you've painstakingly looked for icons to have a mouseover effect to know where your cursor is long enough!  way better support in 3.19.0 kernel but also more instability with boot and freezing-up.  the only way to use it long term is to have it charging, though, and it charges in 3.19.0 if you can get it to boot with AC adapter plugged in the whole time.  it stinks to have to give up stability for increased hardware support.  wifi compiles OK on 3.19.0 and touchscreen works without compiling, but wifi won't compile on anything newer than that that I've tried so far (maybe would in 64bit, not 32 though).  I really like Vivid Mate, I just wish I could charge on default kernels.  Will soon compile Android Kitkat kernel in 64bit Vivid Mate, but I have to do it in 3.19.0 to use AC charging.  If you don't have to compile Android kernel or something, you're better off with 32bit.  I'm finally at the point I was at with 32bit in 64; I found out you need 64 for KitKat kernel the hard-way!  :-)

---

### Post by huwwevans on 2015-03-11
I've been trying this but although the tablet Boots from USB I can't actually install any Ubuntu OS.  Ubiquity just hangs on install.  It takes about 5 minutes to get to the partition options and then it always crashes at some point during the install.  Usually when installing the kernel or gnome power manager but there doesn't seem to be a huge amount of pattern.  

Is there an alternative way of installing that doesn't require Ubiquity?

---

### Post by Jesse_Hofseth on 2015-03-12
huwwevans, you could create USB installer using Lubuntu 15.04 alternate install iso, then you wouldn't have to use ubiquity:
[http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/)
or you could use Lubuntu 14.10 alternate install iso for USB installer.  Lubuntu is the only flavor left that provides alternate iso's nowadays--that I know about, at least.  Good luck!  :-)

---

### Post by huwwevans on 2015-03-14
Ok, I tried lubuntu 15.04 alternate and I can boot it.  Problem is my USB keyboard doesn't work once the kernel loads so I can't do anything.  (it's a keyboard only interface so no idea if the mouse works)  The only clue is the line i8042: no controller found as the kernel boots.  Apparantly this refers to old PS/2 keyboard controller.  

Any idea how to get it to look for my usb keyboard?

---

### Post by Jesse_Hofseth on 2015-03-15
> **huwwevans said:**
> Ok, I tried lubuntu 15.04 alternate and I can boot it.  Problem is my USB keyboard doesn't work once the kernel loads so I can't do anything.  (it's a keyboard only interface so no idea if the mouse works)  The only clue is the line i8042: no controller found as the kernel boots.  Apparently this refers to old PS/2 keyboard controller.  

Any idea how to get it to look for my usb keyboard?
not sure.  I would boot with externally-powered hub with that or a different USB keyboard plugged in.  I used both 32bit and 64bit Vivid MATE 15.04.  Sometimes using keyboards and mice without the externally-powered hub either locked it up or the USB keyboard/mouse wouldn't be recognized.
1) boot to Lubuntu alternate install with USB keyboard with externally-powered USB hub
2) same as 1) but with different USB keyboard and/or different externally-powered USB hub
if that doesn't work, I'd re-try downloading current Vivid Mate 32bit iso, etc.  Vivid Mate 32/64 both installed OK for me, then I downloaded 3.19.0 Vivid kernel/headers (both all headers and arch specific headers) from ubuntu mainline kernel PPA.  you have to update to recent kernel if you ever want to be able to charge via booting with AC adapter plugged-in.  Wi-fi just wouldn't compile for me on kernels more recent than 3.19.0 in 32bit and I never tried more recent kernel than 3.19.0 wi-fi compile in 64bit.  32bit is better due to low ram.  Good luck!  :-)

---

### Post by c.emc on 2015-03-18
I've never been able to fully boot Ubuntu  [IMG]http://psg.i.lithium.com/i/smilies/16x16_smiley-sad.gif[/IMG] I've tried everything and I get stuck everytime with this emmc error... I've tried lots of Ubuntu rom, 32bits... 64 bits... 14.10... 15.04... And even different USB key... Disabled secure boot...

I would really love to have Ubuntu on this tablet... Any idea ?

---

### Post by Jesse_Hofseth on 2015-03-20
c.emc, if you follow my tutorial on page 1 exactly, you'll be able to boot USB and successfully install.  Good luck!  :-)

---

### Post by andreasehrle on 2015-03-25
I installed 14.10 without problems but upgraded to 15.04 and the table will not boot with the 3.19. kernel. The old 3.16. kernel boots fine, but has no support for touchscreen and wifi. I tried upstart, systemd and recovery boot options.
Is there a work around?

---

### Post by kerry_s on 2015-03-25
> **Jesse_Hofseth said:**
> haven't tried elementaryOS, but consider the kernel version as you need one of the most recent kernels to support a Baytrail tablet.  Freya is still beta and it uses the same kernel Ubuntu Trusty used:3.13.  I recommend Ubuntu Mate Vivid due to low ram and it's closer to current linux kernel.  If you install 3.19 kernel on top of Vivid Mate you get battery recognition, charging if booted with AC adapter and touchscreen works, but you still gotta compile wifi driver as detailed above.  Trust me, you want a recent kernel with a Baytrail tablet!  Good luck!  :-)


there is a elementary os with a 3.16 kernel.
i386:
[http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-i386.20150312.iso/download](http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-i386.20150312.iso/download)
amd64:
[http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-amd64.20150312.iso/download](http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-amd64.20150312.iso/download)

source of files:
[http://sourceforge.net/projects/elementaryos/files/unstable/](http://sourceforge.net/projects/elementaryos/files/unstable/)

---

### Post by Jesse_Hofseth on 2015-03-30
andreasehrle, you installed both types of headers for 3.19.0, right?  For default 15.04 you have to compile wi-fi and touchscreen each time you upgrade a kernel.  If you successfully boot into 3.19.0, touchscreen will work automatically but you'll still have to compile wi-fi.  For 3.19.0, sometimes you'll have best luck with USB keyboard + externally-powered USB hub through 3.19.0 recovery.  I haven't tried absolute latest kernel from Ubuntu mainline kernel PPA, I just know some of the versions after 3.19.0 did not allow successful wi-fi compile in 32bit, at least.

Really, the only reason for manual install of 3.19.0 is to enable charging when boot with USB A/C adapter plugged-in.  It's less stable than default 15.04 kernels, and the only other benefit is you don't have to compile touchscreen.

---

### Post by andreasehrle on 2015-03-30
I tried kernel 3.19.0-10-generic today and the tablet shuts off by its own before I can read the log output. I tried all options in the boot menu. So my problem is not comiling missing driver but simply boot the tablet with a newer kernel than 3.16.

---

### Post by Jesse_Hofseth on 2015-04-04
andreasehrle, at this point I am giving up on Ubuntu with HP Stream 7, because the default kernel even on 15.04 is still too old and I'm tired of instability with manually installed recent kernels.  I'm in the process of downloading from [http://torrent.fedoraproject.org](http://torrent.fedoraproject.org)   Fedora 22 Alpha Mate.  I'll probably still need to modify the UEFI folder to boot from USB (due to HP Stream 7 32bit firmware), but we'll see.  Obviously, this is an Ubuntu Forum, so I won't be posting about Fedora stuff.  I'm sad to leave Ubuntu, as its package management is superior....it's just too old with respect to kernel and Baytrail tablets absolutely need recent kernels.  Good luck.

---

### Post by Tyler_Slabinski on 2015-04-04
I've successfully installed Linux on an HP Stream 7, but I've been having a lot of trouble with the touchscreen. It constantly sends button events whenever I touch it at all. The onscreen keyboard types multiple letters per touch, it's impossible to drag windows, and I can't even press any buttons without it at least double-tapping.

I did an evtest and it appears the touchscreen is rapidly sending BTN_TOUCH->0 and BTN_TOUCH->1 events whenever I touch it.

Is anyone else having this issue? I've had the same issue with Fedlet, Ubuntu, and Arch.

---

### Post by vik6 on 2015-04-04
Could someone who successfully made a good image post it on [http://www.distroshare.com](http://www.distroshare.com) ?

It would be really useful for everyone !

---

### Post by Jesse_Hofseth on 2015-04-06
I recommend Fedora 22 Mate with Compiz (alpha 3) due to something like ~4.0.0 kernel for better Baytrail support.
[http://torrent.fedoraproject.org](http://torrent.fedoraproject.org)
Use *fedora live USB installer only*
Then place this 32 bit efi binary:
[https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi](https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi)
into the live USB's  /EFI/BOOT/ directory
and create a grub folder within /boot directory to make /boot/grub/
Then, copy grub.cfg into /boot/grub/ directory, because the 32bit efi binary looks for grub.cfg there.
Then, modify copied grub.cfg by removing efi from linuxefi and initrdefi to make just linux and initrd.  
Power off.  Boot into boot options F9; boot from USB.  You see grub menu now and can boot live installer.  Select troubleshooting and select low graphics mode in grub menus.  Within installer, you have to select EFI partition to be used as /boot/efi/.  (I recommend first resizing Windows in Windows.). I recommend used as normal partition with ext4 for one partition of free space to be used as / (root) partition.  In Windows (later) you have to edit the EFI partition by pasting the same 32 bit binary (above) into the fedora folder containing the 64bit efi binaries.  You also have to create a /boot/grub folder in the root of the EFI partition, and copy grub.cfg into same.  As above, in the copied grub.cfg remove efi from linuxefi and initrdefi to make linux and initrd.  
Power off.  Boot into boot options F9; boot from EFI file; go into fedora folder and select bootia32.efi.  Voila!  Boots OK, touchscreen works, batter indicator works....you still need to compile Wi-Fi driver as detailed on thread page 1.  Good luck!  :-)

---

### Post by DigiAngel on 2015-08-29
I can't get the touchscreen to work at all...did the mod install and it shows up in lsmod, but it just doesn't seem to work on mine.  Anyone have advice for this?  Thanks.

---

### Post by Sandgoose on 2015-08-29
I can boot the usb and had touchscreen working... once, then it crashed, the 6 other boot attempts result in the system locking up at various points during the boot process.

using xubuntu 14.04 i386, any suggestions ?

edit: read more, Not sure how anyone is "running" linux on this tablet, seems hit and miss as to if it wants to boot up at all same with mate 15, interested that support is on the way... eventually ? who's working on this and when is it expected ? in the meantime is there anything I can do to make windows 8.1 less invasive and annoying? talking bart PE levels of OS tampering to strip wanted features and junk ? :D

Thanks

---

### Post by litemint on 2015-09-17
> **kerry_s said:**
> there is a elementary os with a 3.16 kernel.
i386:
[http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-i386.20150312.iso/download](http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-i386.20150312.iso/download)
amd64:
[http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-amd64.20150312.iso/download](http://sourceforge.net/projects/elementaryos/files/unstable/elementaryos-unstable-ltsenablement316-amd64.20150312.iso/download)

source of files:
[http://sourceforge.net/projects/elementaryos/files/unstable/](http://sourceforge.net/projects/elementaryos/files/unstable/)

thanks for this link, works fine on my part, I will just charge my tablet and explore it later on.

---

### Post by Kale_Freemon on 2016-01-08
Unfortunately, I find this to be completely useless. Ubuntu will not boot on the HP Stream 7 at all. It just keeps turning my tablet off (not even shutting down properly - just turns right off during boot). Honestly, Ubuntu is still worthless on tablets. Thanks HP for that one.

Anyone else have this problem too? If so, how'd you get around it?

Yes, Windows still boots up fine.

---

### Post by Bucky Ball on 2016-01-08
> **Kale_Freemon said:**
> Unfortunately, I find this to be completely useless. Ubuntu will not boot on the HP Stream 7 at all. It just keeps turning my tablet off (not even shutting down properly - just turns right off during boot). Honestly, Ubuntu is still worthless on tablets. Thanks HP for that one.

Anyone else have this problem too? If so, how'd you get around it?

Yes, Windows still boots up fine.

You'd improve your chances greatly by starting your own thread. This hasn't seen action for four months. Good luck.

---

### Post by Kale_Freemon on 2016-01-08
> **Bucky Ball said:**
> You'd improve your chances greatly by starting your own thread. This hasn't seen action for four months. Good luck.

I was hoping to avoid making too many threads about the same thing. lol But, if I need to, I shall.

---

### Post by Bucky Ball on 2016-01-08
This thread is about many things, a general chin-wag about Ubuntu and HP Stream 7 by the looks of it (it has drifted quite radically). You *appear* to have a specific problem. If you want help with that problem, post a lot more detail in a new thread than you have here about what's going on, what you've tried, and while we understand your frustration, omit disparaging comments about OSs and hardware manufacturers. They won't get you far but will lessen your chances of support. If you post in a support area, remember, it is a support area, not a discussion one. :)

Good luck.

---

### Post by huwwevans on 2016-01-13
> **Kale_Freemon said:**
> Unfortunately, I find this to be completely useless. Ubuntu will not boot on the HP Stream 7 at all. It just keeps turning my tablet off (not even shutting down properly - just turns right off during boot). Honestly, Ubuntu is still worthless on tablets. Thanks HP for that one.

Anyone else have this problem too? If so, how'd you get around it?

Yes, Windows still boots up fine.
I have been messing around with this for the last year.  Let me explain what I have found.  

There is an official kernel bug (I can't find the link now) that prevents linux from working on the HP stream 7.  It is a KERNEL bug and effects EVERY linux distribution.  The bug creates a loop where the kernel is trying to read a read protected memory block and fails to do so.  

This is the source of just about every problem I have had with installing ubuntu, debian, or mint on the HP stream 7

Sometimes it's the installer that gets stuck (ubuntu server installer) sometimes it's the live install (ubuntu live install) sometimes I install and then it crashes (debian multiarch).

However the root cause is always the same:  The bug is related to 3x 4mb blocks of memory in the HP stream 7's SSD.  all three blocks are in RPMB format and the linux kernel can't deal with them.  

I did get debian running with KDE because the Debian multiarch installer has been patched (or so I guess) to ignore the rpmb partitions.  However once it is installed with a GUI  (I used KDE) the system in prone to crashing, once again due to the RPMB.  

These partitions can't be deleted without a password for decryption, They can't be mounted.  

Until the Linux kernel is patched we won't be able to run any distribution of linux on the hp stream 7 tablet.  

Hope this helps.

Edit: [https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1456443](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/1456443)

---

