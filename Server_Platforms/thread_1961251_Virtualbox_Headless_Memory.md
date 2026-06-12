---
title: "Virtualbox Headless Memory"
date: 2012-04-18
forum: Server Platforms
---

### Post by monarck on 2012-04-18
Our server is currently running FreeBSD with jails, but I have more experience with Ubuntu and would love to switch over.  I've done a bit of research on the virtualization options for Ubuntu and saw that running VirtualBox in headless mode is pretty popular.  The only problem is that our server is fairly limited in terms of memory and power.  We only run about 35 websites so we don't exactly need too much power, but I'm worried that VirtualBox would be too heavy.  On average, how much memory would a single instance require under Ubuntu (with the virtual OS also being Ubuntu)?  

The "busiest" jail runs stuff like Apache, PHP, MySQL, etc.  I'm sure jails in FreeBSD are more efficient since they don't actually require an operating system, but I would love to move to a true virtual machine environment since it would be extremely portable and easy to backup/restore.

---

### Post by Gyokuro on 2012-04-19
Hi,

maybe a KVM server is better suited for you in terms of memory/cpu usage as virtualbox due to the great developer work and support of RedHat and ton's of other companies and it's well tested and used. You can find more information here: [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM) or directly at: [http://www.linux-kvm.org/page/FAQ](http://www.linux-kvm.org/page/FAQ) which should cover most of your questions.

---

### Post by CharlesA on 2012-04-19
+1 to KVM. I've been giving 1GB of RAM to any guest that I am running under VBox

---

### Post by monarck on 2012-04-20
Well, I've checked out KVM a bit and it seems that our processers don't support the KVM extensions, which from what I've read would be make the virtual machines much slower.  In this case, would it really matter if I chose VirtualBox or KVM?  Without that CPU-level hardware virtualization, it seems as it if would be about the same.

---

### Post by CharlesA on 2012-04-20
I think all the enterprise grade VM software requires hardware virtualization enabled. Vbox should work ok if you don't have it.

What are the specs of the machine you are trying to use?

---

### Post by rubylaser on 2012-04-20
The other option would be to use [Proxmox]("http://pve.proxmox.com/wiki/Main_Page") and use [OpenVZ]("http://wiki.openvz.org/Main_Page") containers.  You don't need virtualization enabled processors for OpenVZ.

---

### Post by kgatan on 2012-04-21
OpenVZ will save you alot of hardware.
 
ProxMox 2.0 was just released and its much more sutible for a production enviroment then virtualbox.

---

### Post by CharlesA on 2012-04-21
> **kgatan said:**
> OpenVZ will save you alot of hardware.
 
ProxMox 2.0 was just released and its much more sutible for a production enviroment then virtualbox.
+1 to that. I really wouldn't want to run VBox in a production/enterprise environment as there are hypervisors better suited to that environment out there.

---

