---
title: "Installing Windows 7 x32 in Ubuntu 13.04 on 2nd hard drive"
date: 2013-05-16
forum: Virtualisation
---

### Post by chmegr on 2013-05-16
I have a System 76 bonobo extreme, with a 60GB main hard drive and a 240GB 2nd hard drive. I currently have my Ubuntu 13.04 OS and files on the 60GB. I wish to create a virtual drive on my 2nd hard drive (the 240GB), and have everything Windows 7 related on there. 

I created a new drive, and have set it up on my 60GB no problem, but I realized it was not big enough to have both OSs on there. I now have done the same procedure only everything windows is on my 2nd hard drive. I get it setup to install windows 7 is fine until it does not recognize the CD drive and says the proper drivers are not installed....

Is this because my 2nd hard drive does not have the Ubuntu OS (and hence the system 76 drivers) on it needed to recognize the CD? Also how can I get this to work?

---

### Post by heiko_s on 2013-05-16
Looks like a real cool system, this System 76 bonobo extreme :).

Now the question: How are you virtualizing your Windows 7? VirtualBox, kvm, Xen, VMware, etc.

Or are you talking about dual-boot by chance?

In general it shouldn't matter where you install your virtualized Windows guest. I find the best way to install Windows is not using a CD (DVD), but to copy the disk to a folder in the local hard disk using the dd command. Open a terminal window and copy/paste:
```
dd if=/dev/cdrom of=win7.iso
```
Your /home/username folder now contains an ISO image of the Windows install disk.

Depending on what you are using - e.g. Virtualbox, etc. - you need to select the ISO file you just created as installation media.

**Warning: The dd command is VERY powerful. if= specifies the _input_ file/partition/disk, of= specifies the _output_ file/partition/disk**. If used incorrectly, especially with sudo (root) permissions, it can wipe an entire disk in a second.

---

### Post by chmegr on 2013-05-17
I am using VirtualBox for virtualization. Thanks, I will give this a shot and see if it allows me to do it once the iso os on my computer.

Thanks again.

---

### Post by chmegr on 2013-05-17
So copying it to me /home/username folder worked, however, it is still giving me the same message, even when I select the downloaded ISO file.

So I start the virtual drive, get into windows, and installation starts (english, install now, etc.), then this comes up:
[U][I]
Load Driver: A required CD/DVD drive device driver is missing. If you have a driver floppy disk, CD, DVD, or USB flash drive, please insert now.

Note: If the Windows installation media is in the CD/DVD drive, you can safely remove it for this step.[/I][/U]

below it prompts me to Browse, OK, or Cancel.

I am not sure what to browse to from here.......

---

### Post by heiko_s on 2013-05-18
See if this helps: [https://forums.virtualbox.org/viewtopic.php?f=8&t=31874]("https://forums.virtualbox.org/viewtopic.php?f=8&t=31874").

It might be a bad Windows disk.

---

### Post by chmegr on 2013-05-20
That was it.....bad download from the disk. Thanks!!!

---

