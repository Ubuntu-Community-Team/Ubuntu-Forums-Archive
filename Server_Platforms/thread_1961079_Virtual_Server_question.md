---
title: "Virtual Server question"
date: 2012-04-18
forum: Server Platforms
---

### Post by neuman1812 on 2012-04-18
Not sure if this is the right place, but I figured id start here.

What Im looking to do is setup a headless server with an OS hopefully some ubuntu varient.. that Is specific to running Virtual servers.   So a Vbuntu?

This server would do nothing but host all my other V-Servers  which include some Windows dev systems and Some Linux systems.   

I would like to be able to select which system I log into from a seperate PC. 

IS this possiable?  Is there anything like this already?

FYI- I know the headless would need series HW to support it, that is not a problem.

---

### Post by Gyokuro on 2012-04-18
Hi

I think you want to setup a KVM server ([https://help.ubuntu.com/community/KVM)-](https://help.ubuntu.com/community/KVM)-) we have running them and they are very handy to setup for different projects or requests from branches.

---

### Post by neuman1812 on 2012-04-18
> **Gyokuro said:**
> Hi

I think you want to setup a KVM server ([https://help.ubuntu.com/community/KVM)-](https://help.ubuntu.com/community/KVM)-) we have running them and they are very handy to setup for different projects or requests from branches.

looks just like what i need.  Thanks!
):P

---

### Post by Cheesemill on 2012-04-18
If you don't mind using Debian instead of Ubuntu then check out Proxmox.

All of the OS and KVM installation is taken care of for you and it has a good web front-end to administrate all of your VM's. I use it as a production solution for a couple of clients.

[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

---

### Post by neuman1812 on 2012-04-18
> **Cheesemill said:**
> If you don't mind using Debian instead of Ubuntu then check out Proxmox.

All of the OS and KVM installation is taken care of for you and it has a good web front-end to administrate all of your VM's. I use it as a production solution for a couple of clients.

[http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

Thanks  I'll give that a try tonight.

---

