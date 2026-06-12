---
title: "Network issues on ESXi 5"
date: 2012-07-21
forum: Virtualisation
---

### Post by Techn0crat on 2012-07-21
Not really sure what's going on here, but I figured I would start here.

I have a number of Ubuntu VMs on ESXi 5.  Each of them are having the same issue.  They are 12.04 or 11.10.

The problem I have is the connection outside the LAN starts a stops.  If I ping say google.com it get the DNS record quickly like there is no issue. But it will have 100% packet loss.  This will last for a few minutes.  Then it will work for a few minutes.  Then stop.  Back and fourth.

It's also not just ping, it will cause FF and apt-get to studder as well.

However if I ping anything inside the network it works perfectly.  No issues.

Sounds like a network issue right?  Well if I go to any of the MS machines on the same host on the same network, it works fine.  Absolutely no issues.

Any machines not on the ESXi also work as expected.

I have tired setting the NIC from type Flexible to the host's adapter E1000 and that made no difference.

Any thoughts?

---

### Post by dcstar on 2012-07-24
> **Techn0crat said:**
> Not really sure what's going on here, but I figured I would start here.

I have a number of Ubuntu VMs on ESXi 5.  Each of them are having the same issue.  They are 12.04 or 11.10.

The problem I have is the connection outside the LAN starts a stops.  If I ping say google.com it get the DNS record quickly like there is no issue. But it will have 100% packet loss.  This will last for a few minutes.  Then it will work for a few minutes.  Then stop.  Back and fourth.

It's also not just ping, it will cause FF and apt-get to studder as well.

However if I ping anything inside the network it works perfectly.  No issues.
.......
Any thoughts?

All VMs do is use the hardware of the host. Use some different network hardware or set the Ethernet port to use 100MB instead of 1GB etc.

Also update ESXi with all available patches except the final "SP1" update (which breaks autostarting of VMs on the free ESXi).

---

### Post by Techn0crat on 2012-07-24
Yeah I think I should give that a shot. It is one of the only things I can think of trying. I will just have to try it next weekend.

---

### Post by dcstar on 2012-07-27
> **dcstar said:**
> 
.........
Also update ESXi with all available patches except the final "update-1" update (which breaks autostarting of VMs on the free ESXi).

The latest ESXi 5 patch fixes the VM autostart issue in the free version (even though it doesn't seem to be mentioned in the update notes, but there is a thread in the VMware forums about it).

It is a bit of a chore having to use one of the CLI tools to update the free ESXi patch by patch, but as they say: "whaddya want for nuthin', yer money back!!!"

---

