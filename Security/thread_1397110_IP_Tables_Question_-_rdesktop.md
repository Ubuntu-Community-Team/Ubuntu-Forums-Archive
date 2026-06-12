---
title: "IP Tables Question - rdesktop"
date: 2010-02-02
forum: Security
---

### Post by BlueTeam on 2010-02-02
I set up a simple firewall on my ubuntu 9.10 system using Firestarter.  I'd like to add entries to the iptables so that I can access a VirtualBox vm hosted on the Ubuntu system and made available on port 3389 (virtualbox allows me to expose the VM in this fashion using the remote display feature).  What are the rules that I need to add to allow the rdesktop through from another machine so the firewall doesn't stop it?  Everything is on my internal network behind a router (not trying to pass through my router from an external ip, not yet anyway).  IP addresses are DHCP, so the connecting machine may come from a range of addresses on my internal network (e.g., 10.0.0.1 to 10.0.0.255).  Searched google, came up with lots of solutions mostly geared for external ip access, but couldn't get any of them to work for my situation.  Thanks.

---

### Post by DGortze380 on 2010-02-02
> **BlueTeam said:**
> I set up a simple firewall on my ubuntu 9.10 system using Firestarter.  I'd like to add entries to the iptables so that I can access a VirtualBox vm hosted on the Ubuntu system and made available on port 3389 (virtualbox allows me to expose the VM in this fashion using the remote display feature).  What are the rules that I need to add to allow the rdesktop through from another machine so the firewall doesn't stop it?  Everything is on my internal network behind a router (not trying to pass through my router from an external ip, not yet anyway).  IP addresses are DHCP, so the connecting machine may come from a range of addresses on my internal network (e.g., 10.0.0.1 to 10.0.0.255).  Searched google, came up with lots of solutions mostly geared for external ip access, but couldn't get any of them to work for my situation.  Thanks.

Firestarter is no longer supported. Try gufw, or just iptables.

To allow all LAN machines access to RDP, replace x.x.x.x with your machines local ip.

iptables -A INPUT -s 10.0.0.0/24 -d x.x.x.x -p tcp --dport 3389 -j ACCEPT

---

### Post by BlueTeam on 2010-02-03
Thanks, this works perfectly.  Just what I was looking for.  I'll check out gufw.

---

