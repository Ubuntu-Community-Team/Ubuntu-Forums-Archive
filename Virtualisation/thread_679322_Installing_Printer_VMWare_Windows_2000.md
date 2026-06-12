---
title: "Installing Printer VMWare Windows 2000"
date: 2008-01-26
forum: Virtualisation
---

### Post by rh10023 on 2008-01-26
I moved to Ubuntu because I wanted to run VMware Server and create Windows 2000 Workstation Virtual Machine so that I can get rid of a computer.  Had been running RedHat and then Fedora for years.  Some reason though I cannot seem to get printing setup to work on the W2K Workstation Virtual Machine.  When starting the virtual machine I get the following error message.

"Parallel port "/dev/parport0" is used by another program (such as another instance of VMware Server) or driver (such as lp).
Virtual device parallel0 will start disconnected."

I am running Ubuntu 6.06 Server therefore I do not have the Ubuntu desktop running so running the CUPS web interface is out of the question.  Can someone point me to a step by step troubleshooting guide so that I can get printing setup on my VMWare VM?

---

### Post by dcstar on 2008-01-27
> **rh10023 said:**
> I moved to Ubuntu because I wanted to run VMware Server and create Windows 2000 Workstation Virtual Machine so that I can get rid of a computer.  Had been running RedHat and then Fedora for years.  Some reason though I cannot seem to get printing setup to work on the W2K Workstation Virtual Machine.  When starting the virtual machine I get the following error message.

"Parallel port "/dev/parport0" is used by another program (such as another instance of VMware Server) or driver (such as lp).
Virtual device parallel0 will start disconnected."

I am running Ubuntu 6.06 Server therefore I do not have the Ubuntu desktop running so running the CUPS web interface is out of the question.  Can someone point me to a step by step troubleshooting guide so that I can get printing setup on my VMWare VM?

Why not just set up Samba on the Ubuntu machine and share the printer that way?

---

### Post by swoll1980 on 2008-01-27
as far as samba it's probably a driver issue. This isn't a answer I like to use or hear but maybe a new printer is a good option at this point I haven't seen a printer with a parallel port in a while

---

### Post by rh10023 on 2008-01-28
I have a Laserjet 3015 AIO.  Like to be able to use the scanner with it and I thought I needed to use Windows.  That is what I have on a PC that I currently have the printer hooked up to.  Trying to use VMware to get rid of one PC.

---

### Post by rh10023 on 2008-01-28
> **dcstar said:**
> Why not just set up Samba on the Ubuntu machine and share the printer that way?

I want to be able to use the scanning function of the LJ 3015 AIO.  The scanning is easier in Windows 2000 than having to do it in Linux.  I have my AIO hooked up to a PC running Windows 2000 and I am trying to use VMware to be able to get rid of the PC.

---

