---
title: "save ip link macvlan interfaces after reboot?"
date: 2012-02-11
forum: Server Platforms
---

### Post by ohshhitscarl on 2012-02-11
Our server has one Ethernet NIC port which is connected to our Ethernet cable modem. We read online that we can create macvlan Ethernet ports linked to the main physical Ethernet port that has its own MAC address and that can be assigned its own static IP.

We created the macvlan Ethernet ports as follows:

ip link add dev mvleth0 link eth0 type macvlan
ip link set mvleth0 up
ip link add dev mvleth1 link eth0 type macvlan
ip link set mvleth1 up

The problem we're having is that when we reboot the server, these ports get deleted and we have to recreate them before we can manage them with ifconfig.

Is there a way to save them so they don't get deleted when power is lost or when the server is rebooted?

---

### Post by ohshhitscarl on 2012-02-15
bump, maybe?:confused:

---

### Post by dlezcano on 2012-02-22
Did you try by adding in /etc/network/interfaces something like:

iface macvlan0 inet static
    address 192.168.1.1
    netmask 255.255.0.0
    pre-up ip link add macvlan0 link eth0 type macvlan

---

### Post by flickerfly on 2013-04-25
Also, you could just put those commands in a startup config and that'll work too. If you can put it in the interfaces file, that'd be much cleaner and preferred, imho.

---

