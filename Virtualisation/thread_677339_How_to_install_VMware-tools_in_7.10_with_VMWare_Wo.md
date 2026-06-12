---
title: "How to install VMware-tools in 7.10 with VMWare Workstation 6.0.2 build-59824?"
date: 2008-01-24
forum: Virtualisation
---

### Post by dustyasher on 2008-01-24
I am trying to install VMWare tools in Ubuntu 7.10.  The compilation completes when I run vmware-config-tools.pl but I no longer have eth0 (it removes it).  Is there currently a way to get this working?

---

### Post by D8TA on 2008-01-26
I am trying to do the same thing with Server 6.0.6 but when I cd to /media/cdrom nothing is there. I have tried to cancel VMware Tools installation and clicking VM| Install VMware Tools but I can't figure out where the tools are? I tried using find -name VMware but most of everything was Access denied. I have used OpenSuse in the past so Debian/Ubuntu is new to me. Any help would be greatly appreciated.

---

### Post by Rizlaw on 2008-02-02
If you go to pages 123-125 of the VMware Workstation 6 user's manual, you will see how to install VMware tools from the command line with the TAR Installer.

In Linux, installing VMware Tools into a guest Linux VM is a little more difficult than doing it in a Windows guest VM.

The important thing to understand, for Linux guest VMs, is that you need to copy the VMware Tools TAR file from the virtual CDrom folder to a new or existing /Temp folder on your Host before you can unzip the TAR file in the /Temp folder and run the installer as sudo. With a Windows VM guest OS, you don't need to go through this extra work.

---

