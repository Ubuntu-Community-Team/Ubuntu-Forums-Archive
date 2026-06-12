---
title: "options for creating VM's"
date: 2014-10-28
forum: Virtualisation
---

### Post by jwanutt on 2014-10-28
I'm wanting to creating vm's to run windows desktop machines on ubuntu 14.04.  what are my best options/approaches?  

I have a Xeon 1231
16 ram
240 ssd

Thanks!

---

### Post by TheFu on 2014-10-29
Don't know about that CPU (you can look up the features)
* KVM
* Xen
* VirtualBox
* VMware Player
* VMware Workstation
* VMware ESXi

Some of these will only allow remote desktop connections. RDP, VNC connections are generally considered too weak to be used over the internet without a full VPN, like openvpn or IPSec. If you are trying to run desktop-on-desktop, then virtualbox is probably the easiest to use and will have the most people here running it.
For server-on-server needs, I would avoid virtualbox and look to KVM or Xen for the higher performance, extreme flexibility and stability.

I think those are all the major options, but there may be more.

---

