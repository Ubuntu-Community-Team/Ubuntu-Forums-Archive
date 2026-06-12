---
title: "Ubuntu Server VM on ESXI?"
date: 2016-01-22
forum: Server Platforms
---

### Post by Mike_Burt on 2016-01-22
I'm currently running Ubuntu Server 14 on my Lenovo TS140 ( i3-4130) it has a boot drive which is 500GB and two 3TB drives running in raid 1. I use this server for plex and storing files that can be accessed across my network and remotely from putty or filezilla. This server has 4GB of memory. I also use webmin to administer the server like for creating new samba shares and updating software packages. My question is can I just install ESXI on the server and do all of the same thing via an vm of ubuntu server? What are the cons of this and is this efficient to do? I also want  to be able to run other vm's while the Ubuntu server is running because that one will be the main one for my home so plex server and my files can be still accessed. Thanks.

---

### Post by newbie-user on 2016-01-22
Yes, you can do all the same things in an Ubuntu VM. The con is that you will be sharing the server resources (cpu, ram, etc) with the host and other VMs. So if your server resource usage is already very high, you might run into problems. The con is also a pro if the server resources are currently underutilized. Since you're running a file server, I'm sure your resources are underutilized. So by using a hypervisor, you'll be able to get more out of your hardware by using the resources more efficiently.

I'm recommend checking out Proxmox to use as a hypervisor instead of ESXi.

---

### Post by MAFoElffen on 2016-01-22
Actually KVM is Ubuntu's default kind of choice for a hypervisor... but I run KVM, vSphere and Hyper-V.  I also do support here and over on the Virtualisation Section of the forum, where this post might get moved (since it has to do with that). 

I can honestly tell you, you can run just about any service on a virtual server, but some services just do not do as well, running on a VM. One "type" of service that seems to suffer inside a hypervisor is File services. It has to do with bottlenecks with I/O and disk access. 

I've been studying hypervisors and performance tuning lately. Those 2 points have been a stumbling block in the past. It's been getting better. VSphere (which ESXi is from) is ahead at the moment in those areas. KVM has been behind in those areas... but the newest pending release has been testing much faster than vSphere. It should release soon.

Me? I run a lot of things in virtual, but files services, but I run on my fielservices and storage manager on native iron. I tried it in virtual and there is just a noticeable difference to me. That may change, but currently...

---

