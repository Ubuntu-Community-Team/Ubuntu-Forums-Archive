---
title: "Guest can't ping/connect Internet"
date: 2018-07-05
forum: Virtualisation
---

### Post by satimis on 2018-07-05
Hi all,

Host Ubuntu 16.04 gnome desktop
Guest Ubuntu 18.04 gnome desktop
KVM

Guest can ping gateway
Guest can ping Host
Host can ping Guest

But Guest can't ping/connect Internet

$ cat /etc/network/interfaces```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto ens3
iface ens3 inet manual

# add bridge ports
auto br0
iface br0 inet static
        address         192.168.8.4
        dns-nameservers 218.xx.xxx.xxx 219.xx.xxx.xxx
        network         192.168.8.0
        netmask         255.255.255.0
        broadcast       192.168.8.255
        gateway         192.168.8.1
        bridge_ports    ens3
        bridge_fd       9
        bridge_hello    2
        bridge_maxage   12
        bridge_stop     off

```

Please help.  Thanks

Regards
satimis

---

### Post by KillerKelvUK on 2018-07-05
Assuming the configure shared was hosts, please can you share the same for the guest?

---

### Post by satimis on 2018-07-05
> **KillerKelvUK said:**
> Assuming the configure shared was hosts, please can you share the same for the guest?
Hi,

There are other Ubuntu 16.04 guests.  They can share the network without problem.

This is a newly installed Ubuntu 18.04 guest.  It can't ping neither yahoo.com nor google.com but it can ping their IP address. I suppose it is the problem of DNS

Regards
satimis

---

