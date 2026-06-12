---
title: "Need More Disk Space in VirtualBox"
date: 2011-05-02
forum: Virtualisation
---

### Post by boomcat on 2011-05-02
I have an HP (64-bit) desktop with Ubuntu 10.10 as the host OS. I have Oracle VirtualBox 4.0.6 and within that I have created a Windows 7 Virtual Machine. I created the VM with 20 gigs of memory, but after a week I have less than 1 gig free and I want to enlarge the Win 7 virtual disk, so I found this Terminal command at the VirtualBox.org website at

[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)

Here's the command:

```
VBoxManage modifyhd /home/dave/VirtualBox\ VMs/Win7/Win7.vdi --resize 60000
```


Now the VirtualBox Manager reports that the size of the virtual disk is 58.59 gigs, but the Windows 7 VM still sees a C: drive of only 19.8 gigs, with only 0.99 gigs free.

How can I fix that?

---

### Post by lmarmisa on 2011-05-03
You have enlarged the virtual disk but you have not modified the size of the partition(s) stored on it.

You have to create a new partition (unit D) using the free space or try to extend your Windows 7 system partition.

So, start the Windows 7 virtual machine and select Start -> Computer (Right button of mouse) -> Manage -> Storage -> Disk Management. Then create a new NTFS partition using the free space of the virtual disk or extend the existing system partition (unit C).

---

### Post by boomcat on 2011-05-03
Thanks for the help.

The problem is solved, but I'm not sure exactly how.

I did the "modifyhd" command, then I downloaded an .iso of gparted and pointed the VirtualBox to that and "booted" within VB. This started gparted within the Win7 environment. I resized the partition with gparted, exited gparted and reset VB to boot the Win7 VM. While booting Win 7 I got an error message: "Windows needs to make a repair to allow your computer to start up. Please put your Windows 7 disk in the DVD drive and reboot."

So I did. And selected "repair" from the Win 7 menu. After a couple of boots, everything was fine. I now have triple the disk space.

Not a solution I would recommend, but ultimately it worked.

Thanks again. This is such a great community!

---

