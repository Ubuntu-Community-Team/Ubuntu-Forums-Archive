---
title: "Im thinking of building a cloud - I have some questions"
date: 2010-11-25
forum: Ubuntu Cloud and Juju
---

### Post by c.r.holm on 2010-11-25
Hi, i mange a computer hall at a university. We support about 200 computers and we have about 7 servers and a disk system with diffrent services.
We had an incident witch made us aware of that different services should be more compartmentalized. 

The problem was that we ran DHCP, DNS, LDAP and SMTP on the same server  and it brought down our entire network when a web based email-client  was hacked and used our SMTP server for bad.

What im thinking of is to build a cloud from the servers and some extra and simply have more VMs with less services on eatch. 

[LIST]
[*]Is it possible to run thoughts kind of core services such as DHCP and DNS on VM or is the cloud itself relying on working DNS and DHCPs?
[*]And what kind of servers and machines can be a part of the cloud? We have some older servers now running Solaris with sparc.
[*]How many servers do i have to dedicate to manage a smaller cloud like this?
[/LIST]
Right now we have about 4 different OS and i want to unit them to one.

---

### Post by kim0 on 2010-11-26
Hi,
Answering your questions to the best of my knowledge

- Yes it's possible to run such services on VMs, however it may not be recommended. In certain configurations "managed-novlan" and "managed" mode the DHCP server is implemented by the front end, so no use to have one in the cloud. That server can configured to serve the rest of the physical network as well. However running that on a VM, would IMO be less reliable

- Speaking for UEC, physical servers that can be part of a cloud only need Intel VT CPU extension (kvm restriction) if you'll be running kvm (which is the case by default). You may run Xen however on older CPUs. You may run open-solaris or solaris for Intel as VMs (not sure how supported that would be however). Sparc machines cannot be part of a UEC cloud

- For a small cloud, you can only use a single physical server as the management front-end node. All other servers would be node-controllers running virtual machines

---

