---
title: "Ubuntu bonding XOR protocol"
date: 2016-04-28
forum: Server Platforms
---

### Post by morningstar.fallen on 2016-04-28
Hi everyone,

I'm trying to set up NIC bonding on server 16.04 LTS using XOR protocol. Unfortunately all deployment examples I can find on internet show only setups with either active-backup or 802.3ad LACP, which are great but useless in my particular situation.

Anybody out there who has actually made the bonding work using XOR. Can you please post a sample setup?

Many thanks!

---

### Post by nerdtron on 2016-04-28
Can you show you Network bonding configuration for Ubuntu? 
From the official docs, XOR is Mode 2 or "balance-xor". See [https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

If I remember correctly the configuration for the configuration for bonding is almost the same for the different modes. You'll just need to change the bonding mode:
```

auto lo
iface lo inet loopback

#eth1 configuration
auto eth1
iface eth1 inet manual
bond-master bond0

#eth2 configuration
auto eth2
iface eth2 inet manual
bond-master bond0

# Bonding eth1 & eth2 to create bond0 NIC
auto bond0
iface bond0 inet static
address 192.168.1.200
gateway 192.168.1.1
netmask 255.255.255.0
bond-mode balance-xor
bond-miimon 100
bond-slaves none

```

Try it first and see if the bonding works.

---

