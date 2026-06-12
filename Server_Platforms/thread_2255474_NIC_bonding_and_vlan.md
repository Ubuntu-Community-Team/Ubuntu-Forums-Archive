---
title: "NIC bonding and vlan"
date: 2014-12-05
forum: Server Platforms
---

### Post by brutalis on 2014-12-05
In Ubuntu Server: How do I bond 2 NICs and join the resulting aggregated interface to a vlan and obtain IP via DHCP?

---

### Post by lukeiamyourfather on 2014-12-05
See this on the community documentation site.

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by brutalis on 2014-12-06
I think it's working with:
```
#em1 is manually configured, and slave to the "bond0" bonded NIC
auto em1
iface em1 inet manual
bond-master bond0

#em2 ditto, thus creating a 2-link bond.
auto em2
iface em2 inet manual
bond-master bond0

# bond0 is the bonded NIC and can be used like any other normal NIC.
auto bond0
iface bond0 inet dhcp
bond-mode 4
bond-miimon 100
bond-lacp-rate 1
bond-slaves em1 em2
```

But how do I assign the bond0 interface to vlan 10 to obtain an IP address via DHCP?
The switch *is* configured for bonding.

---

### Post by nerdtron on 2014-12-06
> But how do I assign the bond0 interface to vlan 10 to obtain an IP address via DHCP?
The switch *is* configured for bonding.

HHHmmm....isn't this assigned on the switch itself? If the ports that the server is connected is on VLAN 10 of the switch, then it is on VLAN 10?

BTW, to check if bonding is active:
```
cat /proc/net/bonding/bond0
```
And you should see bond0 on your ifconfig.

---

### Post by brutalis on 2014-12-06
Thanks for the tip. The switch's ports were not set up for the proper vlan. Problem solved.

---

