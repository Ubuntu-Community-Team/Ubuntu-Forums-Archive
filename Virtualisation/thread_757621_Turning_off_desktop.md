---
title: "Turning off desktop"
date: 2008-04-17
forum: Virtualisation
---

### Post by keith_mm on 2008-04-17
Hi
I'm a Linux noob , and I am running ubuntu in a virtual machine as a folding@home client.Is there anyway of turning the desktop off, removing some of  the load off the processor,so that i just run at the command line, and can then easily turn on the desktop when I need to download and install new versions.
 Thanks

---

### Post by AlphaWu on 2008-04-17
System--System Management--Services
Uncheck GDM.

When you want the Gnome,just type "startx".

---

### Post by atcronos on 2008-04-17
If you are using VirtualBox, you can use VirtualBox VRDP to run the virtual machine in headless mode and then SSH to run the whatever program you want.

To use this method you need forward a port from your virtual machine.

---

### Post by HermanAB on 2008-04-17
Just change the runlevel.

To turn off the X11 system:
$ sudo init 3

To turn it on again:
$ sudo init 5

---

### Post by StOoZ on 2008-04-17
or with the keyboard : CTRL+ALT+BACKSPACE to turn off when logged in.

and turn on : startx

If I remember correctly

---

### Post by keith_mm on 2008-04-18
thanks , I did the first response and had a mini crisis when the VM failed to respond after a reboot, luckily I had forgotten to click inthe window to activate  the keyboard.logged in and all running ok.

---

### Post by HermanAB on 2008-04-18
Note that ctrl-alt-backspace will restart X.  It doesn't stop it.

The correct way to stop X is to change to run level 3 as shown above.

Cheers,

Herman

---

### Post by DonQuichote on 2008-04-19
I have a virtual machine at my office (very convenient, because it is located at right IP address for all kinds of firewall issues) and I only use it through XDMP over SSH. That basically means that I do use graphical programs with X (but the machine I am sitting at does provide it) and never use a desktop. Even Windows programs running on Wine work this way.

So I disabled screensavers, compiz and all that kind of stuff. This results in Gnome-Desktop to be removed, but I did not experience any issue with that.

Anyone who wants to setup a similar link to virtual machine, please not that SSH has compression options and they can greatly improve a connection over the big internet.

---

