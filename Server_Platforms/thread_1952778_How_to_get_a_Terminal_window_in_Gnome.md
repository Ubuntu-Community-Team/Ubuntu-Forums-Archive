---
title: "How to get a Terminal window in Gnome?"
date: 2012-04-04
forum: Server Platforms
---

### Post by jimerman on 2012-04-04
I'm fairly new to Ubuntu.  I have Ubuntu Desktop, on which I installed Virtual Box, and created a VM where I have installed Ubuntu Server.  In an effort to get a GUI, I installed Gnome.  Now, the VM will only boot to Gnome, and there is no Terminal option in the menu.  I tried to add my own, but I can't find "gnome-terminal" and it seems no matter what I do, I can't get any of the commands I find throughout the file system to open a shell window.  If I press Ctrl-Alt-F1 thru F7, it switches the terminals on the host machine, not on the VM.  I don't want to have to wipe the VM and reinstall, there's got to be a way to get it to launch a command line window.

Alternatively, if I do start over, I am thinking my steps would be to install Ubuntu, then install gnome-desktop, gdm, and gnome-terminal before running gdm, right?

---

### Post by jimerman on 2012-04-05
BTW, I found a blog that said how to install Gnome, here's the link:  [http://cduu.wordpress.com/2011/11/27/install-gnome-on-ubuntu-11-10-server](http://cduu.wordpress.com/2011/11/27/install-gnome-on-ubuntu-11-10-server)

---

### Post by jimerman on 2012-04-05
Dang, figured it out.  I rebooted the VM, and during the boot menu booted into recovery mode, at which point I did the sudo apt-get install gnome-terminal.  Bummer that wasn't included in the base package!

---

### Post by haqking on 2012-04-05
Server is not meant to have a GUI, and if you choose to add one then Gnome is a poor choice as it is really heavy.

And to access terminal

ctrl+alt+t

should work in all flavours if you cant find the shortcut to terminal.

---

### Post by Cheesemill on 2012-04-05
If you are using VirtualBox then HOSTKEY+F1 - HOSTKEY+F7 will switch virtual terminals on your VM.

If you haven't changed it then HOSTKEY is the CTRL key on the right by default.

---

