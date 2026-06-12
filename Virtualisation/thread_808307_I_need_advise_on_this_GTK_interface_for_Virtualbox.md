---
title: "I need advise on this GTK interface for Virtualbox"
date: 2008-05-26
forum: Virtualisation
---

### Post by Bou on 2008-05-26
Hi,

There is a GTK frontend for virtualbox on the works, and I have made several proposals. I need you to take a look at how the interface is supposed to look like, and tell me if you can think of a common option that is missing, or an option that is not necessary but I left there, or any other improvement that you can think of.

Thank you in advance.

[img]http://img151.imageshack.us/img151/7404/pantallazo1bie7io2.png[/img]

[img]http://img214.imageshack.us/img214/958/pantallazo1qp0lq2.png[/img]

[img]http://img151.imageshack.us/img151/3026/pantallazo2ao1mx4.png[/img]

[img]http://img214.imageshack.us/img214/9470/pantallazo3wo2oh4.png[/img]

[img]http://img151.imageshack.us/img151/4923/pantallazo4ww5ym4.png[/img]


[IMG]http://img182.imageshack.us/img182/4434/pantallazo5tn0.png[/IMG]

[IMG]http://img60.imageshack.us/img60/8730/69604983nc0.png[/IMG]

[IMG]http://img252.imageshack.us/img252/2089/56802914lc3.png[/IMG]

---

### Post by kxmas on 2008-05-26
why reinvent the wheel?  the bundled interface is built on mozilla's xpcom which I believe is complied against gtk anyway.

---

### Post by |{urse on 2008-05-26
Personally I welcome this as the builtin interface tops my cpu for a bit before even running a virtual machine. Looks good! Can i get the source?

---

### Post by bradmkjr on 2008-05-26
Great job so far... 

If you are willing to release a deb package I would love to do a write up and promote it on my virtualization blog, [http://x86v.com](http://x86v.com), when it is ready.

Next, a few questions:

After using Virtual Center, a VMware product, for sometime I think the best feature is the cpu/memory utilization information it provides, have a look at VMware server MUI it is a web interface which allows you to see the overall system usage of cpu and memory along with individual VM's. If you could take the system monitor information and display it that would rock.

Could you have drag and drop iso mounting? I would love to drag an iso file to a vm and have it mount it AUTOMATICALLY, or even a cd?

Did you forget about the floppy drive? I know they don't get used very often, but there is a few times they are needed, especially for drivers in a windows VM.

How about a control panel for Virtual Box USB? that has to be the worse feature is getting USB devices to work in VB? if you could have a USB device list, along with some toggle options that would be a huge improvement. Somehow create a USB manager, similar to cd image manager. If it could drag a thumb drive to a VM and have it automatically mount the drive as a usb thumb drive?

How about this? a USB to fold emulator? I would love to see virtual box (or any VM) have a usb thumb drive as a shared folder system. Imagine that inside of the VM folder is a symlink or a folder called shared thumb drive, with is actually emulated into the VM as a usb thumb drive storage device? Maybe even allow all VM's to share 1 USB thumb drive?

Ok, this maybe a ton more work then you wanted, but you asked for it.

Great Work, Keep it Up
Bradford Knowlton
[http://x86v.com](http://x86v.com)

---

### Post by Bou on 2008-05-27
> **bradmkjr said:**
> Ok, this maybe a ton more work then you wanted, but you asked for it.

It's not work for ME, anyway :) I can't program for my life, I'm just trying to give the guy some interface ideas. I'll give him your ideas, though.

> **bradmkjr said:**
> If you are willing to release a deb package I would love to do a write up and promote it on my virtualization blog, [http://x86v.com](http://x86v.com), when it is ready.

At the time there are two files available, a .py and a .glade file, fully functional. We'll try to make an actual .deb, though.

> **bradmkjr said:**
> After using Virtual Center, a VMware product, for sometime I think the best feature is the cpu/memory utilization information it provides, have a look at VMware server MUI it is a web interface which allows you to see the overall system usage of cpu and memory along with individual VM's. If you could take the system monitor information and display it that would rock.

I'll tell Fran, but his interface is actually just a wrapper for the CLI so, for the time being, he can only do anything you can do through a command.


> **bradmkjr said:**
> Could you have drag and drop iso mounting? I would love to drag an iso file to a vm and have it mount it AUTOMATICALLY, or even a cd?

That would be actually very cool. I'll tell him.

> **bradmkjr said:**
> Did you forget about the floppy drive? I know they don't get used very often, but there is a few times they are needed, especially for drivers in a windows VM.

There IS a floppy drive, in fact. I put it under "devices", not settings along with the HD and DVD drive, because I wanted to keep the settings tab simple and stick to the essentials, only those options that you NEED to get the VM working.

> **bradmkjr said:**
> How about a control panel for Virtual Box USB? that has to be the worse feature is getting USB devices to work in VB? if you could have a USB device list, along with some toggle options that would be a huge improvement.

Well, I don't really have experience using USB on Virtualbox but any device with configuration options is supposed to have a "configure" button alongside, which would spawn a configuration dialogue. Is that what you want?

> **bradmkjr said:**
> Somehow create a USB manager, similar to cd image manager. If it could drag a thumb drive to a VM and have it automatically mount the drive as a usb thumb drive?

How about this? a USB to fold emulator? I would love to see virtual box (or any VM) have a usb thumb drive as a shared folder system. Imagine that inside of the VM folder is a symlink or a folder called shared thumb drive, with is actually emulated into the VM as a usb thumb drive storage device? Maybe even allow all VM's to share 1 USB thumb drive?

As long as it can be done through the CLI, there's no reason not to. But I'm not sure that's the case :confused:

|{urse, you can download the files [here]("http://forums.gentoo.org/viewtopic-p-5104434.html#5104434").

---

### Post by Bou on 2008-06-03
Just wanted to let you know the project just got a homepage: 

[http://www.xente.mundo-r.com/narf/vboxgtk/](http://www.xente.mundo-r.com/narf/vboxgtk/)

Also, version 0.2 was just released.

---

### Post by Vadi on 2008-06-03
I do hope that the "Mange VDIs" button has an informative tooltip, because a new user will have no idea what a VDI is.

Looks good otherwise tho, I'll try it out.

---

### Post by atlas95 on 2008-08-19
Bump !
Do you know how to compil virtualbox in hardy without default gui, for just use vboxgtk...

Thanks...

---

