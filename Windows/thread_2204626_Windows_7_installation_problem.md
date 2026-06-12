---
title: "Windows 7 installation problem"
date: 2014-02-09
forum: Windows
---

### Post by ilikecolors on 2014-02-09
So I want to replace Ubuntu with Windows 7 (ill get ubuntu back later). I made a bootable USB in Unetbootin and I rebooted my PC. I pressed esc to open the bios and I select my USB. However, one option comes up and thats "Default". Absolutely nothing happens if I press on Default. Also, on the bottom, there is a message that says "Automatically booting in 10 seconds...." but when it gets to one, it goes back to ten. What do I do?

---

### Post by Portaro on 2014-02-09
Unetbootin cant make bootabe WIndows usb.
Use Winusb ->
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

---

### Post by ilikecolors on 2014-02-09
> **Portaro said:**
> Unetbootin cant make bootabe WIndows usb.
Use Winusb ->
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

I just tried that like right now. I got a huge list of errors that just kept growing and growing but if I look into the USB some documents have been added. Should I risk it, or buy a new USB to try it with, or try again?

---

### Post by ilikecolors on 2014-02-09
I found out the reason that Unetbootin doesn't work is because that if the USB isn't formatted as FAT32, it simply doesn't accept it. So is there any older bersions of Unetbootin that might work?

---

### Post by Bucky Ball on 2014-02-09
Just format the stick as fat32 in Gparted and try again. No older versions that are any different in this respect.

Let's get this straight: You are attempting to burn Win to a USB with this or Ubuntu? It is unclear.

---

### Post by ilikecolors on 2014-02-09
Okay, im trying to burn Windows to a USB to replace Ubuntu.

Now, News Flash: I got it to work with Unetbootin 494 yet when I select the USB in my BIOS, I get a problem that says "BOOTMGR is missing". I guess my .iso file is corrupted???

---

### Post by Bucky Ball on 2014-02-09
*Thread moved to **Other OS/Distro Support**.*

As mentioned, you should be using Win software to do this.

---

### Post by ilikecolors on 2014-02-10
Alright new method. I used GParted to NTFS format it and I also installed Winusb. However, at the beginning of the process, I tend to get a error that it can't access the media or something. At the end, I end up with a list of errors that keeps getting bigger and bigger. What do?

I should probably mention, in GParted Partiton Editor, when I select my USB, theres also another section called "unallocated". I don't think its normal.

And, besides the errors, some files do get added to the USB. Should I do it anyway?

---

### Post by Portaro on 2014-02-12
Hum , Winusb do a format partition by default, you dont need format usb with other tools.

Unetbootin version 491 , I think which this version can make a windows 7 burn but im not assure if work.

You can try install ntfs -3g and then try to format the usb with NTFS filesystem and then burn the ISO.

Try sudo winsub to see if works.

And of course you have a manual method with dd command-> 
[http://superuser.com/questions/671332/how-to-burn-a-windows-iso-to-my-usb-flashdrive-in-ubuntu-12-04-lts](http://superuser.com/questions/671332/how-to-burn-a-windows-iso-to-my-usb-flashdrive-in-ubuntu-12-04-lts)

---

### Post by Bucky Ball on 2014-02-12
> **Portaro said:**
> 

You can try install ntfs -3g and then try to format the usb with NTFS filesystem and then burn the ISO.


You don't need ntfs-3g to do this. Gparted will format it as NTFS regardless. The OP did just that not more than a couple of posts ago ...

> **ilikecolors said:**
>  I used GParted to NTFS format it ...

---

