---
title: "VMWare fullscreen problem"
date: 2008-12-02
forum: Virtualisation
---

### Post by ScubaSteve84 on 2008-12-02
Hi,
I'm using VMWare Workstation 6.5, and I'm trying to switch over from Windows XP, to Ubuntu 8.10 x64 as the host system. The trouble is, fullscreen/exclusive mode doesn't seem to be working properly on the Ubuntu host.

What I want is to run a Windows guest in fullscreen or exclusive mode, and have my actual (host) screen resolution change whenever I change the guest resolution. This happens automatically on the Windows host, but on the Ubuntu host it just centers on the screen with black borders.

I've tried using fitHostToGuest in the VMWare config, but that just stretches out the guest without changing the host resolution. I'm not sure if this is a VMWare issue or Ubuntu issue or just my own lack of experience with Linux, but if anyone knows how to fix this or at least point me in the right direction, I'd really appreciate it.

---

### Post by beameup on 2008-12-02
Sounds like you need to install VMWare Tools. It's included in the software. It's a menu item that mounts a virtual Cd  in your host and you install from there.

---

### Post by ScubaSteve84 on 2008-12-02
Sorry, I should have mentioned that I already have tools installed in the guest. This happens with all Windows guests even with vmware tools installed, I'll try setting up a Linux guest to see if it happens there as well.

update: The same problem occurs with Ubuntu 8.04 as guest, so I'm guessing it's an issue with the host setup. FYI, I'm running 8.10 fully updated, kernel 2.6.27-9, Nvidia driver 177.80, Gnome, no compiz.

---

### Post by beameup on 2008-12-03
I suppose you've browsed through the vmware forums already. That would be my next step.
I'm pretty much a newbie to the VM thing. Man, the days of triple booting are over. :D:D:D

I run VMWare on my Mac Mini. My Ubuntu box is hooked up to the VGA port on the same monitor, so I can have them both on at the same time, just flip the monitor from DVI to VGA.

Anyway, hope you get that solved.

---

### Post by Dedoimedo on 2008-12-03
Maybe you are trying resolutions that are not supported by your host?
Dedoimedo

---

### Post by ScubaSteve84 on 2008-12-03
Thanks for the replies. I've seen quite a few posts about fullscreen in Virtualbox, but not so much with VMWare - all the more reason I think it's something to do with my setup.
The resolutions I am trying to use are 640x480 and 1024x768, both of which are  selectable in System->Preferences->Screen Resolution, or in the nvidia-settings app. When I set the host resolution to one of these myself, VMWare has no problem with it, but it should be able to set the correct resolution automatically.

---

### Post by mpf on 2009-03-14
For a windows Host OS and Ubuntu as you guest OS:

Go to ubuntu menu, and select:

systems>preferences>screen resolution>Resolution 

you can select the size of screen that best fits you computer. 

Hope it helps.

MPF

---

