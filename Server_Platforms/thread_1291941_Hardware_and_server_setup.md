---
title: "Hardware and server setup"
date: 2009-10-15
forum: Server Platforms
---

### Post by Asheguy79 on 2009-10-15
I am learning to programme with Ruby and also learning Ruby on Rails. I have learned that I will have to have both the Apache and MySQL server packages to be able to store my Ruby projects and to run my Rails projects.  Here is the problem though I have only one computer and have to use it as the house desktop as well as a server if it is possible.  I would just build a server but I am out of work so money is a little short right now.  So my question is can I run a desktop and server on one computer with these specs?

Intel Core 2 Quad Q8200@2.33 GHz
8 GB of RAM
3 1TB SATA Western Digital Caviler Black hard drives.  They run at 7200 rpm and have two processes each.
1 320 GB Western Digital Caviler Blue hard drive @ 5400 rpm SATA
NVIDIA GeForce GT 120 PCI-E 16x video card with 1 GB dedicated RAM @ 550MHz.
NVIDIA as is my bridge and just about every other control on my motherboard.

Also should I set up a raid or use LVM's?  Any help would be greatly welcomed, I am new to alot of this and am having to learn as I go.

---

### Post by volkswagner on 2009-10-15
What operating system are you currently running?  Your system sure could handle several virtual machines, which may be perfect for your development server.

---

### Post by Asheguy79 on 2009-10-15
I am running Ubuntu 9.04 Jaunty Jackolope

---

### Post by volkswagner on 2009-10-15
There are several choices.

As I already stated create VM server using your choice of virtualization software, such as [KVM]("http://www.linux-kvm.org/page/Main_Page"), [Virtualbox]("http://www.virtualbox.org/"), [VMware Server]("http://downloads.vmware.com/d/info/datacenter_downloads/vmware_server/2_0"), etc.

If you take the extra work you will be greeted with yet several more choices in prebuilt VM OS's.  Such as [JeOS]("http://www.ubuntu.com/products/whatisubuntu/serveredition/jeos"), [TurnKeyLinux]("http://www.turnkeylinux.org/appliances"), etc.

You could install the necessary packages on your desktop environment, as in [this]("http://www.ubuntugeek.com/installing-lamp-using-taskeldesktop-edition.html") how to.

You could also use a packaged setup such as [XAMPP]("http://www.apachefriends.org/en/xampp-linux.html") for Linux.

Another possibility is to dig out an old PC, free, cheap or otherwise.  If you install Ubuntu Server, an old Pentium 2 with 256Meg of RAM (even less RAM will work fine) will be all you need.  Once setup, you can administer it remotely, so no keyboard, mouse or monitor will be needed.

---

