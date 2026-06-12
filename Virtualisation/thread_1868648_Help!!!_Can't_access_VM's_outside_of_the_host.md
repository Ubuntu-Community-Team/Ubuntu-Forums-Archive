---
title: "Help!!! Can't access VM's outside of the host"
date: 2011-10-24
forum: Virtualisation
---

### Post by domonics on 2011-10-24
Hey guys I need some help. I'm sure someone somewhere has done this but for the life of me I can't get this to work.

This is what I want to do:

Setup a server that acts as gateway/router/dhcp server and to host virtual appliances using VMware player (or any vm server/player) for my home network using two (2) ethX cards. One nic is connected to my ISP (eth0, using dchp from isp cable modem) and the other connected to my switch (eth1, providing ipaddress for connected computers). I would like to be able to access the vm's remotely either by a computer on the network or via the internet.

Now the gateway/router/dhcp is working fine, the other computers and devices on the network are getting access to the internet (using iptables). And i'm able to access the webmin interface for the server remotely (using ddclient and DyDNS).

What i cant do is access any of the vm's outside the host machine. I have tried using "bridged" on the vm's but it will only go to eth0 and an ip wont be issued. As for the vmnetX i'm only seeing vmnet1 and vmnet8 (NAT and Host Only) which were created from the VMware Player install.

As i said earlier I'm sure some has done this already, i just can't find the info to get it done.

Here are the specs of my server:

> Ubuntu 10.04 LTS
VMWare Palyer 4
2 GB Ram
Intel Celeron Dual Core 2.6
500 GB HDD
Running LAMP


If you need anymore info let me know and thanks in advance.

---

### Post by b0b138 on 2011-10-24
I think you need to have your vms use eth1, so they'll get an address like any other physically connected computer.

---

### Post by domonics on 2011-10-24
> **b0b138 said:**
> I think you need to have your vms use eth1, so they'll get an address like any other physically connected computer.

That's what want to do but don't know how to do that. There isn't an option in VMware Player 4 that allows you to use an ethX card other than eth0

---

