---
title: "kvm/kvm cluster web console"
date: 2014-05-28
forum: Virtualisation
---

### Post by kira_belka2 on 2014-05-28
Hi everybody!
Well I faced with a trouble of choice:guitar:
I have 2 host servers for virtualization..
And I need create HA cluster within failover.
What's best choice for it?
So I choose kvm/lxc as virtualization engines.
also I used virsh/libvirt.
Thanks for all possible help and advices.

---

### Post by TheFu on 2014-05-28
There are many different types of HA clustering. The best/safest types completely depend on the services being protected. Without that, we cannot really help.
Also which KVM/LXC are you using? THAT matters too.

For most web servers, an active-active setup works best using DNS failover and a set of reverse proxies.
For most DB servers, an active-failover setup works best - the DB used matters, since different DBs have different ways to accomplish this. Heck, different sorts of workloads will lead to a different sort of DB cluster.  So for things like social media crap, active-active can probably work. Updates will not be to the same records, so collisions are unlikely. OTOH, for many business apps, active-failover makes more sense to prevent collisions that cannot be reconciled later.

Does this make sense?  There are good books on cluster designs, but most of the time it is best to avoid those unless there is lots of money on the line and plenty of budget to accomplish the solution properly.  IMHO.

---

### Post by kira_belka2 on 2014-06-11
Well there are a lot "realization"s of a several mechanisms for HA cluster management. 
So just two basis way. first one is application layer clustering.
And next one is vm level clustering.
For example: I can use mysql cluster software and  other hand I can try to create HA cluster for two nodes with non-cluster mysql server.
Same with tomcat. 
.. 
I asked about analogue of proxmox pve cluster for example..
And I have one hard restriction.. I use two node cluster((

---

