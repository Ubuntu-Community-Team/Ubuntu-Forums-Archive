---
title: "Trying to install Windows and delete Ubuntu (Ubuntu 14.04) (AMD) (64x Bit)"
date: 2014-12-17
forum: Windows
---

### Post by gmendelson1030 on 2014-12-17
Hello, I have been trying to install Windows 7 onto my laptop. I have the iso image on my laptop. I have made the partition table msdos, Made my usb a nfts, and format my usb to nfts. But when ever i go to install windows on Unetbootin it wont detect my usb it doesnt show it. Please help me.

(I am not so familiar with Ubuntu so try to the instructions simple)

Sincerely,
              
              Gabe

---

### Post by nerdtron on 2014-12-17
Unetbootin will not create a bootable windows USB installer.

You need tools:
Windows 7 iso
Windows 7 USB DVD tool download from microsoft: [http://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool](http://www.microsoft.com/en-us/download/windows-usb-dvd-download-tool)
Windows 7/Vista/XP computer to use the DVD tool

Then instructions are also on that link.

---

### Post by gmendelson1030 on 2014-12-17
what if you dont have a win 7 pc to install it on :/

---

### Post by yancek on 2014-12-17
> Hello, I have been trying to install Windows 7 onto my laptop.

If you are trying to install windows, you should be posting at a windows forum or at the microsoft support site.   As stated above, unetbootin is designed to create bootable "Linux" systems and will not work with windows.  You need to get some type of windows software to do that.  Are you trying to create a bootable usb flash drive from which to install windows?  If so, check the microsoft site or a windows forum.  It can be done if you have a windows OS.  You can boot a Linux iso file directly with Grub but that won't work with windows.

> what if you dont have a win 7 pc to install it on :/         

Not sure what you mean by that.  A PC is just the hardware on which you can install various operating systems, windows, Linux or others.  
You might clarify exactly what you are trying to do with more detail.

---

### Post by nerdtron on 2014-12-17
> **gmendelson1030 said:**
> what if you dont have a win 7 pc to install it on :/

I don't know of any linux program that can create a bootable windows 7 USB.
Found this link which is a bit complicated: [http://thornelabs.net/2013/06/10/create-a-bootable-windows-7-usb-drive-in-linux.html](http://thornelabs.net/2013/06/10/create-a-bootable-windows-7-usb-drive-in-linux.html)

---

### Post by gmendelson1030 on 2014-12-18
I got a friend to get me a bootable disk now i need to make an nfts partition on my hard drive. 

I tried unmounting it in gparted but it says this:
[FONT=book antiqua]
[I][B]The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.[/B][/I][/FONT]

Once i have installed windows on my computer how can i then delete ubuntu from my computer? Or does it automatically delete Ubuntu from my computer?

-Gabe

---

### Post by nerdtron on 2014-12-18
> **gmendelson1030 said:**
> I got a friend to get me a bootable disk now i need to make an nfts partition on my hard drive. 

I tried unmounting it in gparted but it says this:
[FONT=book antiqua]
[I][B]The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.[/B][/I][/FONT]

Once i have installed windows on my computer how can i then delete ubuntu from my computer? Or does it automatically delete Ubuntu from my computer?

-Gabe

You are using gprated on your Ubuntu? Partitions that are in use can't be reformated. You should manipulate partitions on a LIVE environment only.

Anyway, if you already have a bootable USB, you should just boot into USB and start the windows installation. Format your hard drives on the windows installer itself.

This is no longer an Ubuntu issue.

---

### Post by Mark Phelps on 2014-12-19
For installation help on Windows 7, please go to [http://www.sevenforums.com]("http://www.sevenforums.com") -- the premier Win7 forums.

---

### Post by oldos2er on 2014-12-19
Moved to Other OS Support and Projects.

---

