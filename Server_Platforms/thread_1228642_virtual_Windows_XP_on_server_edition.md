---
title: "virtual Windows XP on server edition"
date: 2009-08-01
forum: Server Platforms
---

### Post by happypolla on 2009-08-01
Hi All,

I want to install a virtual windows xp machine on my ubuntu server (8.04). I've installed the various tools etc. but when it comes to installing xp, it fails because there is no desktop manager and I can't run the virt-viewer.

I would like to avoid installing a full-fledged desktop manager as that somewhat defeats the purpose of installing server edition in the first place, can somebody point me in the right direction?

Thanks,
Kohei.

---

### Post by Meatshield on 2009-08-01
What packages did you install to get it ready to virtualize?

In my experience something like VMWare Server is a good solution. It's a free, all-in-one, web-based virtualization scheme. I use it mainly because most things just work with it, including various Linux distributions that fail in VirtualBox. Plus you don't need an x-server to run it since it's web based.

---

### Post by happypolla on 2009-08-01
I've been following: [https://help.ubuntu.com/8.04/serverguide/C/libvirt.html](https://help.ubuntu.com/8.04/serverguide/C/libvirt.html)

so, i've installed kvm and the various other packages outlined there.

---

### Post by jamesrfla on 2009-08-01
I think that VMware Server is what I have been looking for. I was looking for a program that I could make a run VM's and be able to do a keyboard combination to change to different VM's. Like press Alt+2 to switch from Ubuntu server edition interface to Windows server 2003 interface. When I looked at this [https://help.ubuntu.com/8.04/serverguide/C/libvirt.html](https://help.ubuntu.com/8.04/serverguide/C/libvirt.html) I got confused. I thought KVM is a little hardware switch you can buy and you just pug it in so you can have 2 desktops on 1 monitor, keyboard, and mouse.

---

### Post by Thirtysixway on 2009-08-02
I'd recommend vmware.  I use it on my headless server, no problem.  It has a web interface to manage the virtual machines.

---

### Post by dipeshmehta on 2009-08-02
Can anyone please throw some light on VMware ESXi?  it is free too.  I want to know the difference between using vmware server and esxi.

Dipesh

---

### Post by jamesrfla on 2009-08-02
With a few Google searches I found out that the VMware ESXi has built in hypervisor. The hypervisor is virtual machine monitor that allows multiple operating systems to run on a host concurrently. So I am guess the ESXi just comes with the hypervisor.

---

### Post by happypolla on 2009-08-02
> **Thirtysixway said:**
> I'd recommend vmware.  I use it on my headless server, no problem.  It has a web interface to manage the virtual machines.

ok, this sounds like good advice.

anything in particular i should take caution with, or should i just install and fire away?

i'm probably going to follow the instructions at [http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/30/install-vmware-server-106-on-ubuntu-804-hardy/) for installation.

---

### Post by jamesrfla on 2009-08-02
Just go and install it. If you have problems just post it in this thread and we will be happy to help you.

---

### Post by jamesrfla on 2009-08-02
I figure out the difference between the VMware ESXi and the VMware Server. The VMware ESXi is basically a operating system that you install on a server and you can manage all of your VM's. If you watch the online demo it might help you understand more. [http://download3.vmware.com/demos/esxi/VMware_ESXi.html](http://download3.vmware.com/demos/esxi/VMware_ESXi.html) The VMware server is like installing a new program on a existing operating system. The only problem with VMware Server is if you have to reboot that operating system you installed the VMware Server on all of your VM's will shutdown too. Having the VMware ESXi prevents that from happening. The one good side about the VMware Server is you won't have to reinstall your operating system you have on your mail server. So in your situation since you don't want to start from the beginning I would go with the VMware Server. Hope this helps.

---

### Post by Thirtysixway on 2009-08-03
The only thing I run into is config issues when I upgrade the kernel of Ubuntu.  I have to do a ./configure sometimes for it to work afterwards

---

