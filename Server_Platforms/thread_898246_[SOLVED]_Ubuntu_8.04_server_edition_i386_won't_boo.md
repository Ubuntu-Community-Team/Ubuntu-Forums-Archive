---
title: "[SOLVED] Ubuntu 8.04 server edition i386 won't boot on a Virtual Box virtual machine"
date: 2008-08-23
forum: Server Platforms
---

### Post by pi.boy.travis on 2008-08-23
I recently installed (for testing purposes) Ubuntu 8.04 server edition i386 in a Virtual Box virtual machine.  Installation was completed successfully.  However, upon reboot, I get the following error:

Starting up . . . 
This kernel requires the following features not present on the CPU:
0:6
Unable to boot - please use a kernel appropriate for your CPU.

When creating the machine I more than satisfied the system requirements.  Isn't Virtual Box an x86 emulator?  Is there another version I should be using?

Thanks in advance!

---

### Post by windependence on 2008-08-23
I'm pretty sure it's looking for virtualization built in to the CPU and you don't have that. This is one problem I have with VirtualBox and one reason I use VMware. Keep in mind that VERY few Intel CPUs have this feature and some AMDs do. At any rate you can try this:

When using sun's virtual box, you can enable PAE/NX in the settings menu. It can be found in the Advanced tab of the General settings.

The Advance option is available when your virtual OS is powered off. Select the OS installed on your virtualBox .First go to setting -->> General-->> Advanced.

Another possible solution:

You can use server installation CD to boot into rescue mode.
After mounting the root partition of the installed harddisk and you get the # prompt, run this command "apt-get install linux-virtual".

This will help you get the linux kernel customized for VM environment.
You might need to run this command if the installation not success - "apt-get build-dep linux-virtual".

Grub menu won't be changed in some cases so you have to edit /boot/grub/menu.lst to boot with the virtual customized kernel.

-Tim

---

### Post by mrsteveman1 on 2008-08-23
> **windependence said:**
> I'm pretty sure it's looking for virtualization built in to the CPU and you don't have that. This is one problem I have with VirtualBox and one reason I use VMware. Keep in mind that VERY few Intel CPUs have this feature and some AMDs do. At any rate you can try this:


Vbox isn't supposed to use VT or AMD-V by default, so it shouldn't be checking for them.

In any case, almost all Core duos have VT, except a few part numbers where it was disabled. All Core 2s have VT, and i think the last few core revs of the P4 have VT as well. 

AMD specs here from wiki: "AMD-V is present in AMD Athlon 64 and Athlon 64 X2 with family "F" or "G" on socket AM2 not 939, Turion 64 X2, Opteron 2nd generation[1] and 3rd generation[2], Phenom, and all newer processors"

---

### Post by thefekete on 2008-08-23
> **windependence said:**
> 
Another possible solution:

You can use server installation CD to boot into rescue mode.
After mounting the root partition of the installed harddisk and you get the # prompt, run this command "apt-get install linux-virtual".

This will help you get the linux kernel customized for VM environment.
You might need to run this command if the installation not success - "apt-get build-dep linux-virtual".

Grub menu won't be changed in some cases so you have to edit /boot/grub/menu.lst to boot with the virtual customized kernel.

-Tim

This is similiar the workaround given in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216784") filed for this issue.

Here's how it was said in that post:
> 
Solution:
boot from the ubuntu-server CD and choose "Rescue a broken system" from the boot menu.

Start a shell exchange the kernel

apt-get update
apt-get install linux-generic
apt-get remove linux-server

This may not be the perfect solution, but it works.

/ Jakob


This seems a little cleaner, and removing the server kernel package should insure that your grub keeps the right kernel between upgrades (YMMV).


-dan

---

### Post by windependence on 2008-08-23
I'm thinking enabling PAE may work for him. I would try that first before mucking with the kernel. Yeah I read the bug report. I don't think they fixed it yet.

-Tim

---

### Post by windependence on 2008-08-23
> **mrsteveman1 said:**
> Vbox isn't supposed to use VT or AMD-V by default, so it shouldn't be checking for them.

In any case, almost all Core duos have VT, except a few part numbers where it was disabled. All Core 2s have VT, and i think the last few core revs of the P4 have VT as well. 

AMD specs here from wiki: "AMD-V is present in AMD Athlon 64 and Athlon 64 X2 with family "F" or "G" on socket AM2 not 939, Turion 64 X2, Opteron 2nd generation[1] and 3rd generation[2], Phenom, and all newer processors"

Yes, you are correct on this. The point I was trying to make (not very well I guess) was that AMD has more processors with VT support. I am probably biased because I am an AMD partner. ;)

-Tim

---

### Post by pi.boy.travis on 2008-08-23
Enabling PAE/NX worked.  Thanks!

---

### Post by de0xyrib0se on 2008-08-23
I posted a solution on this over 3 days ago in the forum, should have searched first :)

---

