---
title: "Newbie, asks advice with KVM"
date: 2009-09-01
forum: Virtualisation
---

### Post by Dave.Wynne on 2009-09-01
I,m in the process of replacing a Windows 2000 server with 2 
Ubuntu 9.04 servers, one very simple. Print/File server also acting as BDC and secondary KDC. The other is PCD, Primary KDC, Apache2, Bynari Insight Server,DNS , OpenLdap, MySQL and a windows installation to act as a licence server.
Obviously I'll need to install windows as a virtual machine, but I was thinking to make a virtual machine for each of the servers, so If there is a problem with one virtual server that can be restarted without dragging down the whole system, but I'm not sure if you can successfully run a system this way, (especially DNS & LDAP)
Dave

---

### Post by bodhi.zazen on 2009-09-01
I think of Virtual Machines as Physical machines.

If your physical DNS server goes down, it affects the whole system.

If your virtual DNS server goes down, it affects your whole system.

You can almost certainly do what you are wanting to do with virtual servers. You may wish to look at something such as Proxmox (OpenVZ + KVM + a web interface to manage your VM).

---

