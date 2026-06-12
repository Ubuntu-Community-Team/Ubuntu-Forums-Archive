---
title: "Best Cross-platform KVM Management Tool"
date: 2010-07-16
forum: Virtualisation
---

### Post by gtdaqua on 2010-07-16
Our Virtualization infrastructure was running on VMWare Server 2.0.1 but I've always wanted to use KVM because its integrated with Kernel and lightweight. But simply put, KVM was a pain to configure 2 years ago and even today its not as easy as installing VMware Server 2.x/1.x.

And getting a management tool is another pain-in-the-a!!. Right now, am using virt-manager on my Ubuntu Lucid desktop. I've to manually edit the XML files to enable VirtIO for HDD and network and that is all fine. But i've to use root login to see the console of the VM or even connect to it via virt-manager.

KVM is great in performance compared to VMware Server. But management tools available are very poor. This is one of the reasons why KVM is not a buzz word. 

Here is a nice link on Management tools available for KVM.
[http://www.linux-kvm.org/page/Management_Tools](http://www.linux-kvm.org/page/Management_Tools)

Most don't work or work after super-heavy troubleshooting. That is the state today. The only thing that actually works is Virtual Machine Manager and if you are using older distros (< 10.04), then that won't work properly either. 

There are so many limitations in embracing KVM. Can any KVM experts suggest a practical application that can manage KVM environments for both Windows and Linux and also that doesn't require us to put root passwords everytime we want to see the console.

Thanks.

---

### Post by naelq on 2010-07-16
since i'm in the same boat, i'm interested too.. subscribed!


nael

---

### Post by sh1ny on 2010-07-16
```
adduser myuser libvirtd
adduser myuser kvm
```

( on the server )

Connect with your user from virt-manager to the machine and voila ! :)

I have around 50 virtual machines spread on 20'ish or so nodes in different deployments and i'm not the only one managing them AND we do not use root password. If you use qemu+ssh to connect with ssh keys you won't even have to type your password at all.

---

### Post by gtdaqua on 2010-07-16
> **sh1ny said:**
> ```
adduser myuser libvirtd
adduser myuser kvm
```

( on the server )

Connect with your user from virt-manager to the machine and voila ! :)

I have around 50 virtual machines spread on 20'ish or so nodes in different deployments and i'm not the only one managing them AND we do not use root password. If you use qemu+ssh to connect with ssh keys you won't even have to type your password at all.


I figured there is something like this. Great! Now, off to "cross-platform". Some of my guys use Windows. How do they work with KVM hosts?

---

### Post by gtdaqua on 2010-07-16
> **sh1ny said:**
> ```
adduser myuser libvirtd
adduser myuser kvm
```

( on the server )

Connect with your user from virt-manager to the machine and voila ! :)



How do we exactly "Connect with your user from virt-manager"? virt-manager by default uses the root username and prompts for the root's password.

Update:
Got it. Specify new connections as [email]username@ip.address.of.kvm[/email]-host instead of just ip address.

> 
If you use qemu+ssh to connect with ssh keys you won't even have to type your password at all.


Can this be achieved via GUI? or is it via using cli?

---

### Post by sh1ny on 2010-07-16
> **gtdaqua said:**
> How do we exactly "Connect with your user from virt-manager"? virt-manager by default uses the root username and prompts for the root's password.

Update:
Got it. Specify new connections as [email]username@ip.address.of.kvm[/email]-host instead of just ip address.



Can this be achieved via GUI? or is it via using cli?


[IMG]http://farm5.static.flickr.com/4076/4799045965_ff3b2ea232_b.jpg[/IMG]

---

### Post by gtdaqua on 2010-07-19
Thanks, shiny. I got that. 

Still left with the great question:

How do Windows Admins administer KVM hosts?

---

### Post by sh1ny on 2010-07-19
> **gtdaqua said:**
> Thanks, shiny. I got that. 

Still left with the great question:

How do Windows Admins administer KVM hosts?

Putty -> ssh -> virsh :)
Or you can try compiling virt-manager/libvirt for windows :)

---

### Post by gtdaqua on 2010-07-20
> **sh1ny said:**
> Putty -> ssh -> virsh :)


That's not gui. Am talking about Windows admins. virsh is for linux admins.

> 
Or you can try compiling virt-manager/libvirt for windows :)
So there  is no ready way to administer kvm hosts from windows. :(

---

### Post by senor_smile on 2010-07-23
This may be out of the scope of what you're looking for, but I recently tried out proxmox as a way of managing my vm's.  I had looked into enomaly, convirt and simply having x sessions on windows machines via putty to manage kvm virtual machines with virt-manager.  

I tried out proxmox and couldn't be happier.  Install is very quick and everything needed to manage my vm's is all available from a cross platform gui.  They even have a built in cluster mode to make one proxmox server the master to administer all other proxmox servers.  This combined with drbd between two proxmox servers is a beautiful thing. You may still have to customize your vm's to get them exactly how you want.  

FYI it runs on debian 5 base with no gui (headless server install).

---

### Post by naelq on 2010-07-23
i've received my hardware (or some of it, to be exact) i did not have enough time to play with it, but here is what i've tried:
> Proxmox, very nice, though i would like it to be using a more recent versions or both the kernel & libvirt..
> Ubuntu Server 10.04, minimal amd64 install with libvirt, managed remotely via another ubuntu 10.04 workstation with virt-manager, no major problems, though still, i would prefer more recent kernel, libvirt & virt-manager
> Gentoo minimal install, with newer kernel, libvirt & virt-manager, again managed remotely with a Gentoo workstation.. feels better! :p

next week, i hope i'll be able to test the system more thoroughly.. will keep you posted :)


nael

---

### Post by gtdaqua on 2010-08-19
Sorry, I was not following this for weeks.

Proxmox is a different setup even though it uses kvm. I want to be able to keep Ubuntu and still manage the VMs from other platforms. Even a basic, start/shutdown-via-gui is good enough to begin with.

---

### Post by pred2k on 2010-08-26
Isn't there still no Web-GUI avalible to manage kvm/virsh?

---

### Post by gtdaqua on 2010-09-21
> **pred2k said:**
> Isn't there still no Web-GUI avalible to manage kvm/virsh?

Apparently, not anything useful yet.

May be is there anything being developed?

---

### Post by z33k3r on 2011-01-20
I'm in the same boat!

Has anybody tried Ganeti? [http://code.google.com/p/ganeti/](http://code.google.com/p/ganeti/)

It has a web GUI as well... [https://code.osuosl.org/projects/ganeti-webmgr](https://code.osuosl.org/projects/ganeti-webmgr)

I believe both are still in development but being used in production as a stable product in most reguards... going to try it out tonight me thinks!

---

### Post by bodhi.zazen on 2011-01-20
Have you tried Proxmox ?

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

[img]http://pve.proxmox.com/mediawiki/images/thumb/1/16/Screen-startpage-with-cluster.png/800px-Screen-startpage-with-cluster.png[/img]

---

### Post by mutrax on 2011-03-25
Sorry for reviving this old thread. But I'm in the process of looking to go away from vmware server 2 , to , probeably kvm (xen is not default in ubuntu, more uncertain future) . So about gui's; This any good? 
[http://www.convirture.com/products_opensource.php](http://www.convirture.com/products_opensource.php)

Plus I see in the repo's there are packages that allow direct vnc to the gues ( without them having vnc installed) Do these work? (virt-viewer)

Is the install/ migration straightforward or are there any caveats . I'm virtualizing a few *buntu and win7 sandboxes. And one lts guest for customer.

---

### Post by JPorter on 2011-06-30
Bump... any new "winners" in this area?

I see a number of web-based tools that skirt the edges of what we're all looking for, but most are either too enterprise oriented (designed for large-scale management) or are non-functional on Ubuntu.

Here's the list, as I understand it currently:

[Virtual Machine Manager]("http://virt-manager.org/") - desktop KVM management client with remote connectivity, currently unable to manage network interfaces on Ubuntu/Debian
[ConVirt 2]("http://www.convirture.com/products_opensource.php") - web-based KVM management, apparently has some problems installing easily on Ubuntu 10.10+
[Proxmox VE]("http://www.proxmox.com/products/proxmox-ve") - full Debian-based KVM server distro with web management


The unknowns:

[OpenNebula Sunstone]("http://opennebula.org/documentation:rel2.2:sunstone") - web-based "private cloud" vm management tool, supports KVM
[StackOps]("http://www.stackops.org/") - OpenStack Nova distribution based on Ubuntu Server 10.04, designed for industrial-scale KVM deployments including clustering and extreme scalability. Seems like overkill but maybe it works?
[Virtualbricks]("http://www.virtualbricks.eu/en/") - desktop management tool, promising features, but has a horrid website


Some nice stuff that won't run on Ubuntu or Debian:

[Karesansui]("http://karesansui-project.info/") - really slick web-based KVM management tool, only for RH/CentOS variants
[OpenNode]("http://opennode.activesys.org/") - bare-metal CentOS-based KVM server distribution with web management

I also eliminated commercial pay-to-play solutions like Solus VM, because they involve paid licensing.  The terms aren't terrible though, I may have to look at that more closely.


Does anyone have any info about any of the above that might be useful?

---

