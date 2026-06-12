---
title: "VMware Tools Install via CLI"
date: 2008-02-06
forum: Virtualisation
---

### Post by BrentC on 2008-02-06
Hi, I am running Ubuntu 7.10 Server Edition. Currently I am trying to mount VMware tools and install it via CLI because I cannot seem to start x-server. 

I installed the latest xorg version from the Ubuntu repos. I'm pretty sure xorg.conf is configured correct except for the mouse. The errors I get while starting x-server relate to not being able to find the "vmware mouse". I figured this problem might stem from not having VMware Tools installed currently. Now, when I try to mount VMware Tools, nothing shows up in the cdrom drive so I can't unpack and install VMware tools. 

Any ideas on how to solve this problem?

EDIT: To clarify any future questions about the VM cdrom, yes it is powered on and yes it is showing up on on the server.

---

### Post by fjgaude on 2008-02-06
Seems to me that these Tools are related the to virtual OS and are installed after the vm is installed. I know this is true for WinXP and for Ubuntu.

---

### Post by BrentC on 2008-02-06
> **fjgaude said:**
> Seems to me that these Tools are related the to virtual OS and are installed after the vm is installed. I know this is true for WinXP and for Ubuntu.

I think you might be confused and think I am asking how to run VMware Tools on the host OS that is running VMware, which I'm not. I am trying to install it on a guest OS installation of Ubuntu 7.10 Server Edition. I'm not sure what you mean exactly when you say "virtual OS" I will assume you are talking about the guest OS, which I did install on VMware. It is Ubuntu 7.10 Server Edition, which by default, doesn't have x-server installed or any window manager. I installed xorg, configured it, and then installed a WM(window manager, Openbox to be specific).

However when I try to start x-server I get multiple errors showing there is no such device as "vmware mouse". This is why I thought the problem was that I needed to install VMware Tools because I am pretty sure VMware Tools fixes multiple mouse, keyboard, and obviously, GPU driver problems.

---

### Post by fjgaude on 2008-02-06
Well, I do understand what you are doing... my comment was meant to point to the fact that one has to be within the guest to add the Tools.

On the systems I've installed VMware server on: the mouse and keyboard all worked without the tools but were slow and jerky. They functioned and could be used but it wasn't pretty. The tools made them work as on the host.

I can't help you with getting xorg working. The GUI of VMware Console in WinXP was always used by me.

Likely there is someone out here that has tried successufully to do what you are trying. Good luck.

---

### Post by BrentC on 2008-02-06
Well I got VMware Tools installed, but still having the same issue with xorg not being able to find the vmmouse drivers. Anyone have any ideas how to install them manually?

---

