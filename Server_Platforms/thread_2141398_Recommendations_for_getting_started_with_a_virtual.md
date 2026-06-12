---
title: "Recommendations for getting started with a virtual hypervisor"
date: 2013-05-02
forum: Server Platforms
---

### Post by flycast on 2013-05-02
We are looking at setting up some new hardware and then running virtual servers rather than physical file servers. We are looking at this for flexibility and to reduce hardware costs, etc.
We are looking for:
[LIST]
[*]GUI management of the virtual servers
[*]Physical to virtual migration
[*]Optional - virtual to physical
[*]Inexpensive
[*]Able to grow
[*]Production environment
[/LIST]
We have looked at VMWare.com and find their site very confusing for first timers. I also know there are other solutions out there some free, some not.

What solutions would you Ubuntu server users recommend?

---

### Post by rubylaser on 2013-05-02
[Proxmox]("http://www.proxmox.com/downloads/proxmox-ve") is a great, free solution that uses both KVM and OpenVZ virtualization technologies. [Openstack]("http://www.openstack.org/") is another solution, but more difficult to setup than Proxmox.  Setting up your fileservers to scale out is very popular too.  [Ceph]("http://ceph.com/") and [Gluster]("http://www.gluster.org/") are two open source options for this.

---

### Post by CharlesA on 2013-05-02
Thanks for mentioning Proxmox. I've heard it recommended quite often but I thought it didn't have a free version, glad I was wrong.

---

