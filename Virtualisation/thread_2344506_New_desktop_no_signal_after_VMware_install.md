---
title: "New desktop no signal after VMware install"
date: 2016-11-25
forum: Virtualisation
---

### Post by singletrack on 2016-11-25
[COLOR=#000000]Hi everyone new here to the forums and my first time using any Linux os 
I just[/COLOR][COLOR=#000000] pieced together a new desktop
[/COLOR][COLOR=#000000]amd 6300
gigabyte 970 mb
[/COLOR][COLOR=#000000]xfc rx480 8gb
[/COLOR][COLOR=#000000]2x 4gb 1600 corsair ram[/COLOR][COLOR=#000000]7200
 segate laptop hdd out of my old gh73
[/COLOR][COLOR=#000000]got 16.04.1 installed and checked to verify all the files. Loaded up fine, rebooted and entered my encryption key. 
[/COLOR][COLOR=#000000]
Then after I apt-get the vm tools I shutdown in the settings menu. [/COLOR][COLOR=#000000]Then it prompts me to enter my encrypted key again and it won't work so I hard shutdown a few times 
[/COLOR][COLOR=#000000]Now i get no signal detected and I can't enter to any bios. [/COLOR][COLOR=#000000]Will anyone help me understand what's going on haha, thank you for your time[/COLOR]

---

### Post by howefield on 2016-11-26
Moved to the "*Virtualisation*" forum.

---

### Post by singletrack on 2016-11-26
I mean as soon as I  boot up, no signal detected with no load or bios screen.

---

### Post by deadflowr on 2016-11-26
It might be me, but it is unclear what is what.
Is the install in a VM or something else?

Was VMWare installed on Ubuntu, or was Ubuntu installed on VMWare?

Also, what vm tools did you try apt-getting?

---

### Post by singletrack on 2016-11-26
> **deadflowr said:**
> It might be me, but it is unclear what is what.
Is the install in a VM or something else?

Was VMWare installed on Ubuntu, or was Ubuntu installed on VMWare?

Also, what vm tools did you try apt-getting?

I installed ubuntu 16.04.1, then I atempted to install VMware even tho I haven't 
installed any drivers.


The only tools I used was the terminal

sudo apt-get update

then I did something like

sudo apt-get open install-VMtools-desktop-y

---

### Post by virtmm on 2016-11-27
You might want to do some more research on Vmware.  Vmware tools is not a standalone program.  So what you did makes no sense and just won't work.  Vmware has ESXi which you install as a host operating system INSTEAD of Windows or Linux.  Once ESXi is installed then you create a VM and install a guest such as Ubuntu. Once the Ubuntu guest is installed you then can install vmware tools on the guest.

It looks like you installed Ubuntu on your machine as the host operating system.  In this case vmware tools simply does not apply.  If you have a host operating system then you may be looking for VM workstation.  This is a virtualization software that is installed on a host.  You can't install workstation through apt-get, it is a commercial product you have to buy/download from Vmware.

As to why you don't get a boot screen anymore (can't enter your system BIOS), that is not a software issue.  That has to be a hardware issue,  Maybe your graphics card is loose or the monitor connection is loose etc.  No matter how badly someone screws up a software install, it typically does not impact teh ability to boot and get into the system bios.

---

### Post by kingneutron on 2016-11-29
>  segate laptop hdd out of my old gh73

Check monitor / VGA cable and graphics card, make sure everything is connected right (try on another PC if possible)

Hard drive may have died of old age, or after hard shutdown. Try checking cables/replacing the drive and post back, this should not be too much since it was a fresh install

---

### Post by alexeyn on 2016-12-01
use of POST card may solve it

---

