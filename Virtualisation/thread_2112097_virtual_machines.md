---
title: "virtual machines"
date: 2013-02-03
forum: Virtualisation
---

### Post by cwblanch on 2013-02-03
Hi,
[INDENT]I've just got a few questions about virtual machines, for one do you need all the system resources for both operating systems? I'm just playing around with it right now, getting used to it, so I'm installing another Ubuntu in the virtual machine and I'm noticing my computer going a bit slower with some pauses.

Is it possible to transfer files between the virtual machine and your...main pc...?

Thats about all I have for now, it really cool that you can have another operating system running inside your main one!

Thanks
[/INDENT]

---

### Post by oldos2er on 2013-02-03
Moved to Virtualisation.

---

### Post by SeijiSensei on 2013-02-03
> **cwblanch said:**
> I'm installing another Ubuntu in the virtual machine and I'm noticing my computer going a bit slower with some pauses.

Installation is a pretty disk-intensive process so it will tend to slow everything down.  In general, the more VMs you have running the slower they will be unless you have lots of memory and a reasonably fast processor.  I rarely run any modern OS with a graphical interface in less than 1 GB; text-mode only systems like Ubuntu server usually run fine in 512 MB. But disk-intensive activities are especially likely to slow things down since they make it more difficult for the other running VMs to access the drive.

> Is it possible to transfer files between the virtual machine and your...main pc...?

If you are using VirtualBox then, yes, you can create something called a shared folder that both the host and guest can access.  I believe you need the extensions pack installed to activate shared folders.  I often simply write to a network share on my server that I can mount from both the host and guest.

---

### Post by cwblanch on 2013-02-07
> **SeijiSensei said:**
> Installation is a pretty disk-intensive process so it will tend to slow everything down.  In general, the more VMs you have running the slower they will be unless you have lots of memory and a reasonably fast processor.  I rarely run any modern OS with a graphical interface in less than 1 GB; text-mode only systems like Ubuntu server usually run fine in 512 MB. But disk-intensive activities are especially likely to slow things down since they make it more difficult for the other running VMs to access the drive.



If you are using VirtualBox then, yes, you can create something called a shared folder that both the host and guest can access.  I believe you need the extensions pack installed to activate shared folders.  I often simply write to a network share on my server that I can mount from both the host and guest.

The extensions pack worked perfectly, thank you.

But I'm having a problem with it recognizing when a usb device is plugged in, it just doesn't see anything at all.
I've already tried looking it up to see if I could find a fix. But I haven't been able to find anything. It seems no matter what I try it doesn't want to see that there are even any usb devices there.

---

### Post by PhilGil on 2013-02-08
> **cwblanch said:**
> But I'm having a problem with it recognizing when a usb device is plugged in, it just doesn't see anything at all.
I've already tried looking it up to see if I could find a fix. But I haven't been able to find anything. It seems no matter what I try it doesn't want to see that there are even any usb devices there.
                                  It's been a while since I've used Ubuntu but I don't think this has changed... The open source Virtualbox version in the Ubuntu repos (virtualbox-ose) does not support USB connections. You need to install the PUEL (Personal Use and Evaluation License) version from the Virtualbox website ([https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)).
 
Also, be sure your user is a member of the *vboxusers* group or USB support will not work.

---

### Post by GameX2 on 2013-02-08
> **cwblanch said:**
> Is it possible to transfer files between the virtual machine and your...main pc...?

SeijiSensei is right, on VirtualBox you need the Extension Pack;
On VMware however (Also availible on Linux, shareware.  You also need to install an extension, being VMware Tools), it's actually a bit easier.  I find VMware much more powerful (Unity Mode kick ass, with the ability of dragging and dropping shortcuts from the VM to your Ubuntu Desktop), but I've recently switched to VirtualBox, VMware can't run smoothly anymore for some reason.

Anyways, VMware also has this feature, but you could simply drag and drop your file.

I should warn you that if you set up a shared folder (On VirtualBox, VMware, or any other) and get a virus on your virtual machine, the virus should be able to go into the shared folder and possibly infect a Windows machine.  Keep that in mind.

---

### Post by |{urse on 2013-02-08
Yep, get the PUEL version of virtualbox , install guest additions, add user to vboxusers

[https://www.virtualbox.org/wiki/Downloads]("https://www.virtualbox.org/wiki/Downloads")

---

### Post by cwblanch on 2013-02-24
> **|{urse said:**
> Yep, get the PUEL version of virtualbox , install guest additions, add user to vboxusers

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Thank you, I got it all working. ):P

---

### Post by howefield on 2013-02-24
For info, you probably do want to get the deb package from the virtualbox website but not for reasons of PUEL vs OSE, that's long gone.

For some time, there has been only one version to which you may add an extension package which itself is subject to the VirtualBox Personal Use and Evaluation License (PUEL).

You can add this package to both the repository and the virtualbox website editions.

---

