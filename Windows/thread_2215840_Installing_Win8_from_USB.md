---
title: "Installing Win8 from USB"
date: 2014-04-08
forum: Windows
---

### Post by stevie3 on 2014-04-08
Hello ,

 I'm having a little issue here.
I have a problem concerning my main computer.
I wanted to delete ubuntu and install windows 8 again the thing is i already installed ubuntu on multiple
computers and i "forgot" to keep windows on one computer.
So what can i do.
So i have a usb stick i put the windows 8 copy on my usb using unetbootin.
But there is a problem why doesn't it start with the system. ichecked the options in bios
but still doesn't work.
Just before that i formated in ntfs the hardrive with gparted (the main hardrive with a ubuntu live usb)
What should i do to easily uninstall ubuntu on my main computer and install windows 8.
I also read about uefi but didn't understand it perfectly.

Thanks in advance

---

### Post by XBNCPRk on 2014-04-08
Windows provides a USB install tool to install a generic copy. After that you will use your product key (hope you have that written down somewhere or that your stickers have fared better than any of mine ever have) to authenticate the copy. 

As far as uninstalling Ubuntu, dont bother, Windows will just overwrite the drive. 

[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by Bucky Ball on 2014-04-08
*Thread moved to **Other OS/Distro Support**.*

> **XBNCPRk said:**
>  

As far as uninstalling Ubuntu, dont bother, Windows will just overwrite the drive. 



+1. The majority of people here want help with their computer, but they get more response with descriptive thread titles. I have taken the liberty of changing yours. Good luck.

---

### Post by stevie3 on 2014-04-08
> **XBNCPRk said:**
> Windows provides a USB install tool to install a generic copy. After that you will use your product key (hope you have that written down somewhere or that your stickers have fared better than any of mine ever have) to authenticate the copy. 

As far as uninstalling Ubuntu, dont bother, Windows will just overwrite the drive. 

[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)


Thanks for your reply but i don't have any PC with windows installed only linux.
So this method is not possible.
I've been trying for one month now.
Each time i turn on my pc and pick in the bios the startup option
"usb" it doesn't start on usb stick it starts in the grub in fact i'm stuck
  inthe grub and i can't do anything 
to conclude i hope some experienced member will help me soon

---

### Post by Bucky Ball on 2014-04-08
PS: It's possibly not booting from the USB because it sees nothing that can boot. Try here:

[http://lifehacker.com/5840252/install-windows-8-from-a-usb-stick/all](http://lifehacker.com/5840252/install-windows-8-from-a-usb-stick/all)

... and download the Win7 USB tool. There is a link there.

---

### Post by oldfred on 2014-04-09
Are you sure you have a full install not an upgrade or repair install?

You may get more/better help on Windows here
 [http://www.eightforums.com/](http://www.eightforums.com/)

But Windows does not correctly see Linux partitions which may be causing part of the issue.

If installing in BIOS mode, you can create a NTFS partition with the boot flag with MBR(msdos) partitioning.

Or if in UEFI, Windows needs a variety of partitions and gpt partitioning.
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
And if UEFI, you can only install the vendors's OEM version to use the internal product key.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by mips on 2014-04-10
> **stevie3 said:**
> Thanks for your reply but i don't have any PC with windows installed only linux.
So this method is not possible.
I've been trying for one month now.
Each time i turn on my pc and pick in the bios the startup option
"usb" it doesn't start on usb stick it starts in the grub in fact i'm stuck
  inthe grub and i can't do anything 
to conclude i hope some experienced member will help me soon

This is actually very easy to do.

You will need gparted, ms-sys & a Win8 dvd or iso image.

Insert your usb stick and open gparted. Delete whatever partitions you have on the device so it's blank. From the menu go Device-->Create Partition Table and select 'ms-dos'. 
Next create a single NTFS partition on the usb stick and set the label to msdos. 
Next right click on the partiton and go Manage Flags and choose the 'boot' option. Apply all settings and exit gparted.

Next you gonna need ms-sys which is no longer available in ubuntu repos so you can try PPA's or compile it from source ([http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download))
PPAs:
64-bit deb package
[https://launchpad.net/~rzr/+archive/ppa/+build/3617308](https://launchpad.net/~rzr/+archive/ppa/+build/3617308)
32-bit deb package
[https://launchpad.net/~rzr/+archive/ppa/+build/3617309](https://launchpad.net/~rzr/+archive/ppa/+build/3617309)

Identify your usb stick with **sudo fdisk -l** then do a **sudo ms-sys -7 /dev/sdX** where 'X' is the device identifier for your usb stick, do not add the number after the letter as that is the partition and we wan't to write to the MBR.

Next insert you win8 dvd and copy the entire contents of the dvd over to the USB stick. If you have a iso image you will have to mount it with the 'loop' parameter or use a gui like FuriusISO to mount it with the loop option selected and then copy the files across.

You can now boot Win8 from the USB stick.

Sorry for the wall of text explanation but it's actually only a few steps you have to which will take you less than 5min (excluding the copy of the dvd to usb)

---

### Post by stevie3 on 2014-09-07
Thanks so much mips

---

### Post by Sasha_Aderolop on 2014-09-09
The easiest way to accomplish this process is to already have your hands on a copy of Windows 8&#8217;s downloadable .iso file &#8211; acquirable by purchasing it from Microsoft itself. If you have a flash drive of the appropriate size (at least four gigabytes or greater, depending on whatever file Microsoft lets you grab), you&#8217;re golden. Insert your flash drive into a USB slot on your system, and then go grab Microsoft&#8217;s Windows 7 USB/DVD Download Tool &#8211; don&#8217;t let the name dissuade you.

Install the app and run it. It&#8217;ll ask you to select an .iso file to be &#8220;burnt&#8221; onto your USB key. Go ahead and select your Windows 8 .iso file &#8211; the fact that it&#8217;s not the right operating system as the tool&#8217;s name has absolutely no bearing on what you&#8217;re doing.

---

