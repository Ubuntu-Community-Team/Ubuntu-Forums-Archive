---
title: "chroot help and suggestions"
date: 2007-01-07
forum: Server Platforms
---

### Post by markymarknz on 2007-01-07
Hi everyone,
I am looking at redoing my webserver and was thinking about making it more secure by using chroot.
I know it is better to have a single server for each function eg webserver, mailserver ....
However I only have 2 machines, one is a dedicated firewall and the other I want to use for serving webpages and also setup email.
I was therefore wondering whether anyone here has any advice about setting up 2 chroots on the same machine, in my case one for apache and the other for postfix. I know there are problems associated with chrooting but wanting to keep things secure.
Is it even worth the hassle of setting them up for what I want to achieve?
Also when you upgrade apache and postfix can you just do it as normal with apt-get upgrade or do you need to do something different if they are in a chroot environment.

Any thoughts/suggestions would be most welcome.

Cheers

Mark

---

### Post by pay on 2007-01-07
Wouldn't a virtual machine like vmware or qemu be easier?

---

### Post by markymarknz on 2007-01-07
> **pay said:**
> Wouldn't a virtual machine like vmware or qemu be easier?

Hi Pay,

I considered that but in terms of security if the apache or postfix daemons were compromised for whatever reason they would be confined to those applications, but if it was a virtual machine then they would have access to the whole root subsystem.
Maybe I'm just being a bit paranoid or whatever but I am just trying to do things securely.
Is it hard setting up a VM in commandline?

Mark

---

### Post by Mike'sHardLinux on 2007-01-07
Sounds to me like you have it backwards. If a server in a VM is compromised, only that VM can be compromised. Not the root subsystem.

I have been trying to get a mailserver going in Ubuntu 6.06. Here's one of Flurdy's (from this forum) how to: [http://flurdy.com/docs/postfix/#conf_mta]("http://flurdy.com/docs/postfix/#conf_mta")
He states that Postfix is chrooted by default. 

I don't know about apache2.

Setting up VMware server on the commandline is easy. I don't know how easy it is to create, configure and run VMs from the commandline. I have VMware server on my server. I also have VMware server on a workstation with a GUI. I connect to the server from the workstation and create, configure and run the VMs. That way is pretty easy because I am using the workstation's GUI.

---

### Post by markymarknz on 2007-01-07
> **Mike'sHardLinux said:**
> Sounds to me like you have it backwards. If a server in a VM is compromised, only that VM can be compromised. Not the root subsystem.

I have been trying to get a mailserver going in Ubuntu 6.06. Here's one of Flurdy's (from this forum) how to: [http://flurdy.com/docs/postfix/#conf_mta]("http://flurdy.com/docs/postfix/#conf_mta")
He states that Postfix is chrooted by default. 

I don't know about apache2.

Setting up VMware server on the commandline is easy. I don't know how easy it is to create, configure and run VMs from the commandline. I have VMware server on my server. I also have VMware server on a workstation with a GUI. I connect to the server from the workstation and create, configure and run the VMs. That way is pretty easy because I am using the workstation's GUI.

Hi Mike,
Thanks for your reply.

> **Mike'sHardLinux said:**
> Sounds to me like you have it backwards. If a server in a VM is compromised, only that VM can be compromised. Not the root subsystem.

In regards to this comment I was meaning that if the VM was compromised it is like the whole (virtual) server is compromised and then all the operations on a normal server could be done. I'm not referring to the underlying root file system of the host but the underlying root file system of the guest.

> **Mike'sHardLinux said:**
> I have been trying to get a mailserver going in Ubuntu 6.06. Here's one of Flurdy's (from this forum) how to: [http://flurdy.com/docs/postfix/#conf_mta]("http://flurdy.com/docs/postfix/#conf_mta")
He states that Postfix is chrooted by default. 

Thanks for the link Mike, I have actually read that already, I found the idea of PostGrey interesting to combat SPAM :)

In regards to your VM setup, do you have a base install of Ubuntu Server and then apt-get install vmware-server? Then access the admin of it through the VMWare-Server program on your desktop?

Thanks for your comments :)

Mark

---

### Post by Mike'sHardLinux on 2007-01-07
> **markymarknz said:**
> 
In regards to this comment I was meaning that if the VM was compromised it is like the whole (virtual) server is compromised and then all the operations on a normal server could be done. I'm not referring to the underlying root file system of the host but the underlying root file system of the guest.
Oh, Ok. That's true. But, you can chroot the server software in the VM, too. Even if you don't chroot, VMs are so easy to backup and restore. A compromised VM could be replaced in minutes.

> **markymarknz said:**
> In regards to your VM setup, do you have a base install of Ubuntu Server and then apt-get install vmware-server? Then access the admin of it through the VMWare-Server program on your desktop?


Yes, that's basically it. The default port is 902, IIRC. On the server, you will have to install some libs related to X. But you don't have to install X.

---

### Post by markymarknz on 2007-01-09
After some more thought I have decided that I will not bother with chroot and go for a vmware/xen implementation.
It will be much less administration for me as this will just be a home server.
Thanks for all your suggestions/comments

---

### Post by envis on 2007-04-29
i am trying to set a second apache/php on a computer that still accesses the main MySQL for performance

how can i install VMware or Qemu in command line?

---

### Post by envis on 2007-04-29
can you run qemu or vmware on a ubuntu server version?

---

