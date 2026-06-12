---
title: "KVM hypervisor on dedicated server with only one physical nic and one public ip"
date: 2014-10-06
forum: Virtualisation
---

### Post by jefkebazaar2 on 2014-10-06
Hello,



I am in progress of setting up a dedicated server with only one public IP and one physical NIC.
I would like to use KVM as hypervisor for this setup.


However, I would like to realize a setup that is similar to this one:
[http://serverfault.com/questions/353...-accessible-ra]("http://serverfault.com/questions/353223/recommended-way-to-setup-a-secure-esxi-environment-with-a-publicly-accessible-ra")

Basically, I want to install a virtual pfsense and put this one in front of the host OS.
So the wan-interface of the pfsense guest would get my public IP, not  the physical host running KVM. (is that even possible that a guest would  get the public ip and the physical host would have an internal IP  behind pfsense?)
To be able to access this host running KVM to manage it over SSH, I  would first want to setup a VPN to pfsense that gives me access to a  private network containing the host.
Basically a similar setup like described in the article above to avoid  putting the esxi vsphere client port open on the internet, but for KVM.

I have been googling for a while to get some info on this, but can't  seem to find something that points me in the right direction. I have the  feeling this is going to be way more complex to setup than the pfsense  scenario.

Any advice from someone, perhaps someone who has already implemented something similar?

Thanks in advance for any help!

---

### Post by TheFu on 2014-10-06
First, just because something is possible, that doesn't make it a good idea. Perimeter firewalls really need to be on dedicated hardware for hundreds of good reasons. A $130 miniPC is fine for pfSense, but you can spend $200 on a PCEngines APU1 box, if you prefer.  For a lab environment, running a firewall inside a VM is fine, but I wouldn't risk my network security in that way.

There are ways to mitigate these concerns by adding another NIC to the machine and dedicating that NIC only to the pfSense WAN interface. That is relatively easy.  It is important that if pfSense isn't on, the network is disconnected. 

Doing this also will prevent the temptation of making any services public for the KVM host.  However, using a libvirt client like virt-manager over an key-based ssh connection from anywhere in the world really is highly secure. Be certain to load fail2ban.  No need for a full VPN for admin access at all. 

BTW - I'm a fan of pfsense. Excellent choice.

---

