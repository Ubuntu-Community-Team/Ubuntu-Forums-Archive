---
title: "Migrate out of VMware ESXi 5.0"
date: 2013-03-18
forum: Virtualisation
---

### Post by Hexxus on 2013-03-18
Hello,

At the data-center I've got 6 ESX hosts running around 40ish total vm's locally not on a SAN box. Recently I paid our normal maintenance license fee's and thought about the wonders that be out there that are open-source. 

I was just wondering if anyone has migrated away from ESX, and how it went converting the images over. I had done a bit of homework on a couple options and of course my vendor is really pushing
hyper-v (they're a gold partner) but I wanted to know how others experiences went.

Personally I'd love to check out Ubuntu's offerings but not sure how that would go with the owner.

Also if this was posted somewhere, I apologize. I did do a search and found a few things but nothing too generalized and some was out-dated.

Thanks!

---

### Post by CharlesA on 2013-03-19
Check out [http://www.proxmox.com/products/proxmox-ve](http://www.proxmox.com/products/proxmox-ve)

I have been moving machines off ESXi 4 to HyperV and it has been a royal pain in the butt.

---

### Post by Hexxus on 2013-03-23
yeah, Proxmox was pretty cool and it seemed to be nice, looked like migrating would be a pain though.  Last question is that I'm looking to build a SAN box and was checking out "OpenSAN" and Starwind iscsi software. Has anyone had any luck with either of those two options in a production environment with 40ish virtual machines?

---

### Post by dcstar on 2013-03-27
> **Hexxus said:**
> Hello,

At the data-center I've got 6 ESX hosts running around 40ish total vm's locally not on a SAN box. Recently I paid our normal maintenance license fee's and thought about the wonders that be out there that are open-source. 
...........

You are aware that VMware offer a free ESXi licence if you don't want all the "bells and whistles" of their paid system?

Management of the VMs and hosts is more complicated but that's what you pay for with the fully licenced product.

---

