---
title: "new installation of ubuntu server 16.04.1"
date: 2016-07-26
forum: Virtualisation
---

### Post by q8devilish on 2016-07-26
hi, i am new to linux, just installed ubuntu 16.04.1 in a hyper-v machine, changed the ip address of the newly ubuntu server everything is fine, during the OS installation of the server i choose open ssh server packages to be installed too so i can remote access it from my network, but the problem is a can ping it from any where in my network but cant connect ssh to it for some strange reason, i checked the sshd service it is up and running, when ever i try to connect using putty in my windows machine the connection fail due to time out.

---

### Post by TheFu on 2016-07-26
NAT or bridged networking in the VM? If NAT, then you need to tell the hypervisor to pass traffic to the Ubuntu system. I find it easier to just use bridged networking.
Oh ... and is ssh listening on the public interface?

Firewalls aren't enabled by default, but if you enabled it with a default DENY rule, you'll need to add a rule to allow ssh traffic on 22/tcp.

I don't know anything about hyper-v. Never seen it used anywhere. Suspect most people here will use virtualbox for desktop-on-desktop VMs and KVM for server VMs. If nobody provides a good answer, might want to ask on the hyper-v forums.

---

### Post by MAFoElffen on 2016-07-27
in hyper -V, you have a few factors. the v-ethernet device in "configure Network devices" is the virtual ethernet device that hyper-v bridges to. In hyper-v itself, you have to setup your virtual swtiches yourself. Their is no default v-switch, so the defualt is "not connected."

In the right pane of the hyper-v manager, with your host selected in the left pane-- Their is a link in the upper right that say "Virtual Switch". Form the diaolg that posps open, their will be 3 options: External, Internal, Private. External is bridge. If selected, you will have to map to a NIC. Just like bridged in Linux. Will be a deciated map to a NIC (will not share with host, so host will no onger get to use it.) Internal, there is an option to share with the host. That is guests can talk with each other and host. Private is guests only.

Is that enough to get you started or do you need more info?

---

