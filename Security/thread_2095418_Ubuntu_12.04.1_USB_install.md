---
title: "Ubuntu 12.04.1 USB install"
date: 2012-12-16
forum: Security
---

### Post by trevoraki on 2012-12-16
[LEFT] 
This is my first post so I'll keep it simple.

I've installed Ubuntu 12.04.1 to a 16Gb usb using Unetbootin. Everything works fine but I want to make sure I'm as secure as possible. 

1. As I wasn't asked for a password during the Unetbootin setup the default user (ubuntu) password is blank. Do I need to change the blank ubuntu password?

2. Should I add another user rather than use the default user (ubuntu) account. If so how do I add the new user to the sudoers group.

I am the only person using the PC.
[/LEFT]

---

### Post by Hungry Man on 2012-12-16
You will definitely want to put a password on it. Once you do that (and add it to sudoers, I guess) you won't need a second account.

---

### Post by trevoraki on 2012-12-16
Thanks for the quick reply. 

The ubuntu user account was already added to sudoers during install.

Thanks.

---

### Post by oldfred on 2012-12-16
If you use unetbootin, then you have the installer version, not a full install.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    
I have a full install in an 8GB partition and another 8GB for data in my 16GB flash drive. Not speedy but functional with a fair amount of RAM so most things stay in RAM and some settings to reduce writes on flash drive.

       Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

    
Really more like any install to a second drive.
       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

    
       Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by C.S.Cameron on 2012-12-16
Welcome to the Forums.

As I recall passwords on a persistent install are quite flimsy, It is easy to mount casper-rw and get at all the data.

[http://ubuntuforums.org/showthread.php?t=1028564](http://ubuntuforums.org/showthread.php?t=1028564)

Better to use OldFred's advice.

---

### Post by trevoraki on 2012-12-17
Thanks Oldfred and CSCameron. I will read the various links and get back to you. I am not that knowledgeable with the various install methods hence my use of UNetbootin. It seemed the only one that would give me what I wanted.

---

### Post by trevoraki on 2012-12-18
I have read through the threads you provided and have done a limited instal of Lubuntu on a 4gb just to test out the procedures. All very good and am now going to make use of my 16gb and instal full Ubuntu.

Thanks again for the info.

---

### Post by oldfred on 2012-12-18
I installed full Ubuntu in 8GB and use the other 8GB as data.

You can probably leave your Lubuntu in the smaller partition as it does not need as much space and use the rest as a data partition. Or use gparted to resize. 

Once you have a full install in a flash drive it is just like any other install. Flash drive is just a smaller drive. 

Did I just say a 16GB flash is a smaller drive. I am afraid I remember the first 5MB hard drive and how huge that was. :)

---

