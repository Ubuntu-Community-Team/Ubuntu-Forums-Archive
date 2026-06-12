---
title: "Where is KVM's default bridge config?"
date: 2013-01-23
forum: Virtualisation
---

### Post by cryptochrome242 on 2013-01-23
Hi,

after installing KVM on Ubuntu 12.10, there is a default bridge virbr0 on the system. Where is the configuration file for that? 

Reason I am asking: I am trying to get a handle on KVM and LXC and most of the guides mention to setup a bridge from scratch. Now I see the Ubuntu kvm package already added one for me, but it doesn't appear to have it's config anywhere in /etc.

Any hints would be appreciated.

Thanks!

---

### Post by TheFu on 2013-01-23
I've never used the default bridge. I think it is user-mode, which means it will be VERY slow. I've always setup a bridge using **brctl**.

My manual bridge is setup in the normal /etc/network/interfaces file.

A quick 'find' found this file: /var/lib/libvirt/network/br1.xml
It seems like what you seek, but it has warnings that you shouldn't be directly changing it.  It says to use **virsh net-edit br1**.

---

### Post by cryptochrome242 on 2013-01-24
> **TheFu said:**
> I've never used the default bridge. I think it is user-mode, which means it will be VERY slow. I've always setup a bridge using **brctl**.

My manual bridge is setup in the normal /etc/network/interfaces file.

A quick 'find' found this file: /var/lib/libvirt/network/br1.xml
It seems like what you seek, but it has warnings that you shouldn't be directly changing it.  It says to use **virsh net-edit br1**.

Thanks!

Did you install kvm from the Ubuntu repository? What did you do with the bridge virbr0 that the package created?

What's really odd is that even the official Ubuntu server documentation says that if you want to use bridged networking, you should create a bridge, yet the kvm package already creates one. It's not mentioned in the docs at all. 

This really confuses me. I need to understand what exactly the kvm package installed and configured, so I can make educated decisions. Yet there is no documentation (or I am blind). The same thing is true for LXC by the way. It comes with a preconfigured bridge (lxcbridge0).

---

### Post by cryptochrome242 on 2013-01-24
Ok, so I found some more information.

virbr0 is the default bridge in KVM. It's not usermode, it's a real bridge, and it does NAT for the guests. The backend is bridge-utils (aka Linux bridges). 

Here is an article with some more info and how to disable it, if needed:
[http://www.cyberciti.biz/faq/linux-kvm-disable-virbr0-nat-interface/](http://www.cyberciti.biz/faq/linux-kvm-disable-virbr0-nat-interface/)

The configuration resides in /etc/libvirt/qemu/networks/default.xml

The bridge can be configured with virsh.

This clears it up for me mostly. I posted it in case anyone else has the same questions.

---

### Post by TheFu on 2013-01-24
> **cryptochrome242 said:**
> Thanks!

Did you install kvm from the Ubuntu repository? What did you do with the bridge virbr0 that the package created?

What's really odd is that even the official Ubuntu server documentation says that if you want to use bridged networking, you should create a bridge, yet the kvm package already creates one. It's not mentioned in the docs at all. 

This really confuses me. I need to understand what exactly the kvm package installed and configured, so I can make educated decisions. Yet there is no documentation (or I am blind). The same thing is true for LXC by the way. It comes with a preconfigured bridge (lxcbridge0).

I ignore the NAT bridge. All my VMs are 1st class citizens on my network.
I started with KVM more than a few yrs ago. Back then, it didn't do any bridging automatically and the defaults were user-mode tunnels.  Also know that bridges are a security concern. You'll want to read up about them if you really care about VMs not seeing other VM traffic - ever. If you run all the VMs on a box, I don't know how much I'd worry.

It is good to see that they've improved it.  KVM and all the support tools are improving fast. A few more years and nobody will need commercial virtualization tools at all.

---

### Post by cryptochrome242 on 2013-01-24
> **TheFu said:**
>   Also know that bridges are a security concern. You'll want to read up about them if you really care about VMs not seeing other VM traffic - ever. If you run all the VMs on a box, I don't know how much I'd worry.


Thanks. I am coming from a VMware background and the security issue is the same there. Common sense is needed when configuring virtual machines :)

Right now I am also struggeling with getting UFW firewall to work properly with KVM. As soon as I enable it, no more traffic passes the bridge. I am guessing that's a configuration issue, but since I am using defaults from Ubuntu, I would suspect they would make it work out of the box. Do you have any experience with this?

Thanks!

---

### Post by TheFu on 2013-01-24
> **cryptochrome242 said:**
> Thanks. I am coming from a VMware background and the security issue is the same there. Common sense is needed when configuring virtual machines :)

Right now I am also struggeling with getting UFW firewall to work properly with KVM. As soon as I enable it, no more traffic passes the bridge. I am guessing that's a configuration issue, but since I am using defaults from Ubuntu, I would suspect they would make it work out of the box. Do you have any experience with this?

Well, **it IS a firewall.** If you enable it, **it blocks all traffic.** That is what it should do.  If you want something opened, then open it in the config - BEFORE enabling the firewall.  The **man page** for ufw is pretty simple.

Which VMware?  ESX, ESXi or one of their toys?

---

### Post by cryptochrome242 on 2013-01-24
> **TheFu said:**
> Well, **it IS a firewall.** If you enable it, **it blocks all traffic.** That is what it should do.  If you want something opened, then open it in the config - BEFORE enabling the firewall.  The **man page** for ufw is pretty simple.

Which VMware?  ESX, ESXi or one of their toys?

ESXi, vSphere etc.

Sure it is a firewall. But even if you allow some traffic, it won't pass it on a bridge. It's a documented "bug". You need to add some stuff to sysctl.conf to make iptables recognize the bridge interfaces (documented here: [http://wiki.libvirt.org/page/Networking#Altering_the_interface_config](http://wiki.libvirt.org/page/Networking#Altering_the_interface_config) and here: launchpad bug number 573461 as well as several blogs). Oddly enough, it's been like this since 10.04 :)

---

### Post by TheFu on 2013-01-24
Ah, so you are running the firewall on the hostOS?  
I use firewalls inside the guests, if I can't block the traffic upstream at the reverse proxy or inside the network equipment. 

I'd assumed that doing it on the hostOS would likely fail and didn't have time to try it out.

Networking capabilities is where F/LOSS virtualization tools really need help to catch up with VMware. I think all the parts are there, just not packaged into a cohesive result.

---

### Post by cryptochrome242 on 2013-01-24
> **TheFu said:**
> Ah, so you are running the firewall on the hostOS?  
I use firewalls inside the guests, if I can't block the traffic upstream at the reverse proxy or inside the network equipment. 

I'd assumed that doing it on the hostOS would likely fail and didn't have time to try it out.

Networking capabilities is where F/LOSS virtualization tools really need help to catch up with VMware. I think all the parts are there, just not packaged into a cohesive result.

Agreed. Networking needs some improvements here. Open vSwitch looks interesting, but doesn't really address what we were discussing.

Yes, I am running the firewall on the host, not the guests.

I only have one (rented) server with one IP address (it's just a personal lab setup), so I need to masquerade outgoing guest traffic and NAT/portforward incoming stuff to the guests. That's what I am currently trying to get a grip on. 

Unfortunately Ubuntu's UFW in it's current state seems to completely ignore the fact that KVM and bridging exists :D  On the other hand, it's probably designed for simple setups, not for advanced networking stuff. Let's see what 13.04 brings onto the table.

---

### Post by TheFu on 2013-01-24
UFW is an extremely simple interface to iptables.  Also, I don't think UFW is made by Ubuntu/Canonical. Of everything you get with Ubuntu, very little is actually created by Canonical.

For what you want, you need to use a different interface OR hand create the rules.  There are lots of books on iptables to help out. I can recommend _Linux Firewalls_ by Rash.

If you planning to run KVM servers, I cannot recommend that you use any non-LTS release, so either make due with 12.04 or wait until 14.04. Interm releases will not be production ready, IMHO.  Those releases are used by Canonical to try new things - some won't make it into 14.04 and some will have huge issues.  With all the changes for UEFI, GPT and SecureBoot, I wouldn't expect anything major for virtualization from Canonical. Any improvements will come from upstream.

---

### Post by cryptochrome242 on 2013-01-24
Thanks, going to check out that book. Also, Shorewall looks interesting.

As for LTS vs non-LTS: Sure thing. However, this is just my lab to learn stuff. So I figured I'd go with the newest release to have up to date KVM.

---

