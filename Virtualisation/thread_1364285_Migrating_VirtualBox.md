---
title: "Migrating VirtualBox"
date: 2009-12-25
forum: Virtualisation
---

### Post by duf on 2009-12-25
Hi evryone,

I have tried to migrate WindowsXP in a VirtualBox from one computer to another. With no success!

Computer 1: laptop (Intel Pentium 4) with Ubuntu 9.10 and VirtualBox 3.0.12 r54655
Computer 2: Tower (AMD Athlon 64) with Ubuntu 9.10 amd_64 and VirtualBox 3.1.2 r56127

What I did:
I copied win.vdi to the harddisk of computer 2. As I could not attached the win.vdi, I cloned this win.vdi with 'VBoxManage clonehd'. When I tried to start WinXP the only thing I got was a screen with some text and the options to start windows with some text and the chooice to start windows in safe mode, or in safe mode without networking, or in safe mode with prompt or to use the last working configuration.

Neither option worked.

As I have on computer 2 a partition (sda1) with WindowsXP, I thaught to use that partition and create a .vmdk disk image file. I added "my_user_name" to the group disk and I could register the disk image file. So far so good.
But when I started WinXP in the VirtualBox the onlu thing I got san a blank screen with  the prompt "grub rescue:"
After searching in th ubuntu forums I found a method using a mbr. I installed with apt-get install mbr and did an "install-mbr".
Again, I tried to start WinXp and now I got a black screen with "MBR 3FA:"

I also tried the method described by Sand Lee, using a grub iso, but of course this failed as Ubuntu 9.10 uses grub2

So after half a Christmass day I still am nowhere.

Does anyone has a solution. I really need Windows as I have several programs that need Windows. It would be fine to run Windows in a Virtual Machine. I hate to dual boot every time in Windows.

Thanks

---

### Post by Dennis N on 2009-12-25
You can export as a virtual appliance:

In the VirtualBox program window, FILE > EXPORT APPLIANCE

Then, it is possible to import the resulting files (2) into another VirtualBox installation using FILE > IMPORT APPLIANCE. 

The files to be imported must be in the same folder.

---

### Post by mathuna on 2009-12-27
IO APIC, is an on board controller which manages the way Interrupts from IO devices is managed.
An IO Apic information usually is hidden from an OS, not sure about Windows. Perhaps it does some sort of static binding with IO devices on its interrupt gates. Take this with a pinch of a salt though .

But once you have enabled IO Apic on a windows install, do not disable it, it can confuse your windows OS.

Therefore similary, once you have installed a Windows VM using IO APIC capability in VMware, it is not trivial to convert the VM to vdi format, with IO apic functionality intact for different makes of the same device. 

No idea what this HAL in WinXP means BTW.
=====================================
[yoostar](http://www.newsday.com/business/review-yoostar-is-a-movie-studio-in-a-box-1.1401673)
[wildlife paintings](http://www.davidshepherd.com)

---

### Post by SecretCode on 2009-12-30
duf, did you get this to work? I've had no problems moving virtual machines - between similar version of vbox, except that the original host was Windows. I didn't even have to clone the vdis - in the new installation of vbox the disk was obviously not already registered so I could register the copied vdi.

As mathuna pointed out you must set the IO APIC property the same way as it was in the original installation. I think it's also important to have the same display memory and settings for 3D etc.

---

### Post by duf on 2010-01-01
Thank you for your answers !

Well, it is partly solved.

As Debbis N pointed in his message, I migrated the my Windows in the original VBox and imported it on my second computor as a new appliance. And this did work.

In reality, the problem is partly solved. My system is dual boot Windows/Ubuntu. I mostly use Ubuntu. But as i have some times to develop PLC's, I do this in a virtual machine, I then transfer the result to Ubuntu and then to my Windows partition.

What I wish to do is using the existing Windows partition in my VirtualBox so that I don't have all those file transfers (i sometimes get an error)

But anyway thanks for the answer, I can now work in Ubuntu and have Windows open<;

---

