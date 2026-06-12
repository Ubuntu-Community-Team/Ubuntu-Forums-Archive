---
title: "VirtualBox remote USB"
date: 2011-10-20
forum: Virtualisation
---

### Post by dhysk on 2011-10-20
I'm trying to connect a smart card reader to my Windows XP virtual machine running on Ubuntu 11.10.  I want to be able to RDP into it from my laptop and be able to use USB devices on my laptop for the VM running on my desktop.

Desktop =
  Ubuntu 11.10
  VirtualBox 4.1.2 (the one from the repos)
    VB is running a Windows XP VM
    All usb devices in question work when on the server


Laptop =
  Ubuntu 11.10
  No virtualBox
  running rdesktop via command line
  Also tried installing Virtualbox with the extentions but still only had rdesktop avialable.


My issue, i think, is I'm running the wrong remote desktop on the laptop.  According to [http://www.virtualbox.org/manual/ch07.html#usb-over-rdp]("http://www.virtualbox.org/manual/ch07.html#usb-over-rdp") you need to run 'rdesktop-vrdp' however I have no such option on either machine.  I assumed that installing virtualbox and its extras would do the trick but it is still not there.

so ware do I get it or how do I install a remote desktop that supports usb for virtualbox?

---

### Post by mrhobbeys on 2011-10-20
Do you have the VB extensions installed?

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

VirtualBox 4.1.4 Oracle VM VirtualBox Extension Pack

Make sure you get the right version.

---

### Post by dhysk on 2011-10-20
yes that is the one I installed.  And the usb as well as the server side of vrde, ie --vrde=on flag, works great.  However I don't seam to have a remote desktop program 'rdesktop-vrdp' on any machine.

---

### Post by mrhobbeys on 2011-10-20
Wait are you trying to run the remote desktop on Ubuntu to connect to another Ubuntu and one of these is inside a virtualbox?

---

### Post by dhysk on 2011-10-20
> **mrhobbeys said:**
> Wait are you trying to run the remote desktop on Ubuntu to connect to another Ubuntu and one of these is inside a virtualbox?

yes,, if I understand what you are saying.

Desktop computer running Ubuntu 11.10 with Vbox installed running a virtual machine that is windows xp

I'm remote desktoping into the virtual machine by

#1. On the desktop(Server) I run this command
```
vboxheadless -s Windows_XP
```
#2. On my laptop running Ubuntu 11.10 i just start remote desktop and connect to 192.168.1.2:3389

This works great but no usb support.  If i plug in my dongle to the laptop the Virtual machine can not see it.

From what I can tell I need to use a different remote desktop client 'rdesktop-vrde'.  I think it comes with virtualbox but I cant find it on the desktop computer or any ware else so I could install it onto my laptop..... why is it so hard to fallow when talking about virtual machines ;)..

---

### Post by mrhobbeys on 2011-10-20
Well VB has problems with USB you need to add it in the VB USB menu, plug it in, restart the VM, once started unplug and replug the USB. It has been a while since I have used USB on VB because of this so that order may be incorrect as far as using the the remote connection you are trying to use is not one I have used before so I really am at a loss on helping you there.

---

### Post by dhysk on 2011-10-20
Thank you for your help though.  But I have usb working great on the desktop.  All the devices I use work there, but using them remotely is the issue.  I'm thinking its because for whatever reason it didn't install the rdesktop-vrde client like it is apparently supposed to.

---

### Post by dhysk on 2011-10-20
ok almost solved.  What I had to do was install vbox from the .deb from virtualbox.org along with the extensions on my laptop. Than add my user to the virtualbox group just like you would on the server.

after that remote usb works great since vbox from the .deb comes with rdesktop-vdrp.  So the only thing I'm looking for now is how to get rid of virtual box exept for the parts i need for rdesktop-vrdp.

I also cant get sound to work via rdesktop-vrdp but it works with rdesktop... ;/

---

