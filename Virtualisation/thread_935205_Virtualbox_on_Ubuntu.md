---
title: "Virtualbox on Ubuntu ?"
date: 2008-10-01
forum: Virtualisation
---

### Post by AgentZ86 on 2008-10-01
Hi

I"m using Ubuntu 8.04 32 bit version

I've installed VirtualBox OSE from the applications/add/remove section
I created a virtual disk per the prompts etc.

Then clicked to start my virtual OS and it said failed:

> Failed to start the virtual machine (Windows XP SP2) which is my virtual drive name etc. 

Then under that error text is says: 
>  
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


Is there something else I need to install ?
Please advise

It seemed pretty straight forward to install and use, but it failed ?

I see in synaptic a bunch of virtualbox virtualbox-ose-modules-generic stuff I could installed but I'm a little nervous about this as to which one I should install ? if any ?

---

### Post by briandu on 2008-10-01
You can install the Synaptic stuff without worrying at all. It will not break your system

---

### Post by silverglade00 on 2008-10-01
Install the virtualbox-ose-modules package that matches with your present kernel. You can find your kernel with 

uname -r

Keep in mind that the virtualbox modules packages lag a little behind new kernel releases, so you will have to be careful to choose your older kernel when you boot up until the next modules package comes out. I have been using it for the last two kernel updates and it takes about a week or so.

---

### Post by hyper_ch on 2008-10-01
```

sudo apt-get install virtualbox-ose-modules-`uname -a`

```

---

### Post by AgentZ86 on 2008-10-01
> **briandu said:**
> You can install the Synaptic stuff without worrying at all. It will not break your system

Thanks,

---

### Post by AgentZ86 on 2008-10-01
> **silverglade00 said:**
> Install the virtualbox-ose-modules package that matches with your present kernel. You can find your kernel with 

uname -r

Keep in mind that the virtualbox modules packages lag a little behind new kernel releases, so you will have to be careful to choose your older kernel when you boot up until the next modules package comes out. I have been using it for the last two kernel updates and it takes about a week or so.


Hi, and thanks

And should I just install the module-generic or should I install all the modules that match my kernel ?

I other words, there are things like:

virtualbox-ose-guest module for linux-image-2.6.24-19-generic
and
virtualbox-ose module for linux-image-2.6.24-19-generic

I'm not sure I understand the guest module vs module ??

Please advise if I should install a bunch of modules or just the one that matches ?

And thanks again

---

### Post by AgentZ86 on 2008-10-01
Hi

Thanks to all for all the help

I've installed this from synaptic:
virtualbox-ose module for linux-image-2.6.24-19-generic

Now I get this:

Failed to start the virtual machine with the following:

> 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

Looks like some permission problem how can I get into this, or did I install the wrong item ?

Should I have installed the one that says guest ?

---

### Post by hyper_ch on 2008-10-01
--> Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

---

### Post by AgentZ86 on 2008-10-01
> **hyper_ch said:**
> --> Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..

I can't figure out where to setting are for this using the VirtualBox GUI

Is this in the GUI or do I have to load some other program to get to those setting ?

I think I see, in Administration/User/Group etc. ?

---

### Post by snova on 2008-10-01
You have to add your user to a group. Specifically, the "vboxusers" group. This is because only members of this group have permission to manipulate a particular file that VirtualBox uses internally.

This isn't something that VirtualBox does. Look for a user management program. I don't know what it's called under Gnome.

---

### Post by AgentZ86 on 2008-10-01
> **snova said:**
> You have to add your user to a group. Specifically, the "vboxusers" group. This is because only members of this group have permission to manipulate a particular file that VirtualBox uses internally.

This isn't something that VirtualBox does. Look for a user management program. I don't know what it's called under Gnome.

I see, thanks, 
I got it figured out now, also I had to set the passthrough for the CD rom and mount that too

I have successfully installed windows xp on virtualbox, and it would appear that my sound/network drivers installed good, but I think my video driver would need installation ?

Do I install drivers the same way I would normally on windows ?

Please advise thanks

P.S I really hate to install windows on this machine at all,I have not used windows in a long time, but there is one trading platform I want to use and I need windows only for a couple months.

---

### Post by snova on 2008-10-02
No. Go to VirtualBox's website and download the "Guest Addons" for Windows XP, and install it into the guest OS. You'll get a lot of useful goodies this way, including a video driver (I think).

---

### Post by AgentZ86 on 2008-10-03
> **snova said:**
> No. Go to VirtualBox's website and download the "Guest Addons" for Windows XP, and install it into the guest OS. You'll get a lot of useful goodies this way, including a video driver (I think).


HI thanks for the reply

I'll look into this thanks.

A few questions I'm considering before doing the (Guest Addons)

What will happen if I install the Radeon ATI driver from my ATI CD as I would normally do within windows ? 
Will it even work ? or is the only way to use(Guest Addons)?
I can't find the guest addons on the site are these guest addons available in synaptic ?


It does actually work currently, but the windows (window) is a bit small and won't fill the screen even when in full mode it's sort of only fits into about 3/4 of the screen sort of a windows inside a window

Anyhow the sound and nic card work well by default

---

### Post by 3rdalbum on 2008-10-03
> **AgentZ86 said:**
> 
What will happen if I install the Radeon ATI driver from my ATI CD as I would normally do within windows ? 

Either a blue screen of death, or no effect. To maintain the integrity of the host operating system, Virtualbox emulates all your hardware except the CPU; it does not pass through instructions unaltered. So according to Windows, you do not have an ATI graphics card, you have a Virtualbox graphics card (or whatever sort of basic graphics Virtualbox emulates).

Same with the sound and LAN cards - Virtualbox emulates them, and any data going to the emulated devices it sends to Linux.

---

### Post by AgentZ86 on 2008-10-03
> **3rdalbum said:**
> Either a blue screen of death, or no effect. To maintain the integrity of the host operating system, Virtualbox emulates all your hardware except the CPU; it does not pass through instructions unaltered. So according to Windows, you do not have an ATI graphics card, you have a Virtualbox graphics card (or whatever sort of basic graphics Virtualbox emulates).

Same with the sound and LAN cards - Virtualbox emulates them, and any data going to the emulated devices it sends to Linux.

Thanks, thats what I needed to know

I see now that the (Guest Addons) are located within the windows of the Windows (VirtualBox) so I just clicked on Guest Addons and it downloaded and installed them automatically

Note: I never actually adjusted my resolution to try to see if this would solve the problem prior to installing the (Guest Addons), but It's working in Full Screen mode now very good.

I don't really know if (Guest Addons) made it work or if simply adjusting my resolution made it work since I did not try the adjustment until after I installed the (Guest Addons) but anyhow thanks for the note on the installing of windows drivers I'm glad I did not attempt it.

---

### Post by AgentZ86 on 2008-10-03
> **snova said:**
> No. Go to VirtualBox's website and download the "Guest Addons" for Windows XP, and install it into the guest OS. You'll get a lot of useful goodies this way, including a video driver (I think).

I see I have it now, thanks

---

### Post by AgentZ86 on 2008-10-03
Ok this is great,

So how does USB devices work ? or do they ?

---

### Post by AgentZ86 on 2008-10-03
One other thing just curious about this?

What is the difference between these 2 modules in synaptic:

virtualbox-ose-guest module for linux-image-2.6.24-19-generic
and
virtualbox-ose module for linux-image-2.6.24-19-generic

I installed _ose module_, what does guest module have or not have that the ose module does or does not have?

Whats the difference ?

---

### Post by snova on 2008-10-03
-guest modules are the Guest Additions, so that you can run Linux as a guest OS instead of Windows. You don't need them, but they'll be good to have if you ever install Ubuntu into VirtualBox.

USB devices work fine, but I forget the magic required to get things set up. But once you do, it's easy.

---

### Post by AgentZ86 on 2008-10-03
> **snova said:**
> -guest modules are the Guest Additions, so that you can run Linux as a guest OS instead of Windows. You don't need them, but they'll be good to have if you ever install Ubuntu into VirtualBox.

USB devices work fine, but I forget the magic required to get things set up. But once you do, it's easy.

Thanks, and once I get the usb stuff working, do I just install my drivers and programs as I would normally for the usb devices ?

Or will I have a problem ?

---

### Post by snova on 2008-10-04
Yes, I think so.

---

### Post by AgentZ86 on 2009-02-06
For my own reference:
Note to self

In Synaptic install > virtualbox-ose module for linux-image-2.6.24-19-generic or latest one that matches your kernel such as: virtualbox-ose module for linux-image-2.6.24-23-generic or 1.6.24-24 etc. and so on, Updates will break this and you will have to install them from synaptic from time to time to keep up with the updates.

Add User permissions

Install Windows XP,

From within the VirtualBox Program Install (Guest) Add-ons

Update ose-module from time to time.

---

### Post by AgentZ86 on 2009-10-28
Additional notes to self

I never could get the USB ports to work on any OEM Virtual box, which is different then the PUEL License from SUN

So simply go to the Sun Site and download the PUEL version for linux host

Located here:
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

And this will give you USB support by default.

FYI

---

