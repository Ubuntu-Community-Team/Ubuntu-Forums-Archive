---
title: "Virtualization making a program seem native"
date: 2009-08-30
forum: Virtualisation
---

### Post by dardack on 2009-08-30
Ok, i lost my bookmarks, and at some point I had one pointing me to a way to have Itunes seem like a native program while running off the virutalization (i use virtualbox).  I can't seem to find this again.

Basically, you can like run a program that runs off the virtualized OS but you don't have the annoying Windows Taskbar.

Anyone know how to do this, or in virtualbox how to completely get rid of the taskbar?

---

### Post by zarthon on 2009-09-01
Since no one else has jumped in here, I'd at least say I have not heard of being able to virtualize windows programs on linux.

You can accomplish this with Linux guest programs on a Windows host by using XMing and among other things User Mode Linux (UML). This is because Linux / UNIX graphic libs are based on the X11 client/server protocol and so each program on the guest OS can be a client to the display server on the host. This of course works with out any add-on on a Linux host.

There is also WINE. Are you certain that you were not reading about one of these ?

I suppose that since VM Ware Fusion accomplishes this with Windows programs on Mac OS X, there is some technical way to accomplish it. It would be very interesting to see your link so if you find it please post it back to this thread.

---

### Post by PilotJLR on 2009-09-02
Sounds like you're looking for VirtualBox seamless mode. That will present individual apps from the guest OS, so it can comingle with your host desktop.

This is an old version Howto, but it will point you the right way:
[http://www.linuxhaxor.net/2008/05/05/creating-seamless-virtual-machine-with-virtualbox-16/](http://www.linuxhaxor.net/2008/05/05/creating-seamless-virtual-machine-with-virtualbox-16/)

---

