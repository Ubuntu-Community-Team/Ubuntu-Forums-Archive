---
title: "Basic help"
date: 2010-08-13
forum: Server Platforms
---

### Post by papershoes on 2010-08-13
I'm a Mac (+Windows) user who is new to Linux. I am not a command-line guru, but I'd like to learn. I have a dedicated server hosted with MediaTemple which uses Ubuntu Server as the OS -this is what made me curious about Ubuntu.

On my home desktop PC, I'd like to start using Ubuntu as my primary OS, but also mimic my dedicated servers environment for learning purposes (eg: I want to learn how to install/uninstall and configure things via the command line, such as Nginx, PHP, MySQL, setting up domains and subdomains etc.)

Should I install Ubuntu Server and then add the Desktop to it or the other way around?

---

### Post by kgeekworking on 2010-08-13
Server and Desktop are basically the same thing.  

The main difference is that server does not include the GUI components and contains a few server-only type features like clustering.  

To just play with the prompt, you can open a terminal from a Desktop install.  All of your basic tasks for installing software, moving around, backing up, etc are the same.

If you want to play around with a server without the risk, you may want to consider to just load it in a Virtual Machine.  VirtualBox is a good desktop Virtual Machine ([http://www.virtualbox.org](http://www.virtualbox.org)).  Load your server image into the VM and take a snapshot of your basic setup.  You can then play around as much as you want without worrying about hosing anything.  If the poop hits the fan, just revert to the good snapshot.

---

### Post by Iowan on 2010-08-13
[This]("https://help.ubuntu.com/community/ServerGUI") *might* be helpful...

---

