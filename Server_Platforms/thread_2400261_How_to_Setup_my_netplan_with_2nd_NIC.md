---
title: "How to Setup my netplan with 2nd NIC"
date: 2018-09-04
forum: Server Platforms
---

### Post by ds-dv on 2018-09-04
Hello Ubuntu Community

I setup a new box with Ubuntu 18.04 server which has 2 NICs.

  The goal is to have a primary nic which goes to a vlan (set by the switch) and the firewall forces all the traffic into a VPN.
The 2nd NIC is for the LAN and should also only be reachable from the lan.
  The problem is that im obviously too stupid to get this running with net-plan.
I searched for a config generator but cant find one.
  Can anybody help me create the config I desire?

  my current config is:
  ```
network: 
version 2 
renderer: networkd 
ethernets: 
enp2s0: 
dhcp4: yes
enp3s0: 
dhcp4: yes

``` 
  thanks for the help!


With kind regards

PPS: is it possible that the nics of the ubuntu system allready ad the VLAN id tags?

---

### Post by darkod on 2018-09-04
Below ethernets, when enp2s0 config lines finish, put enp3s0 and put its config lines (dhcp, static ip, etc). Be careful to use the spacing at front for each line (indendation). They tell netplan how to use the parameters and what is what...
For vlans I'm not sure it's automatic. Google how to use vlans with netplan.

---

### Post by ds-dv on 2018-09-04
> **darkod said:**
> Below ethernets, when enp2s0 config lines finish, put enp3s0 and put its config lines (dhcp, static ip, etc). Be careful to use the spacing at front for each line (indendation). They tell netplan how to use the parameters and what is what...
For vlans I'm not sure it's automatic. Google how to use vlans with netplan.

i guess im too stupid :(
but thanks for the hint with the spaces

to be honest i dont understand why they switched away from ifdown ... it wass all so simple

---

### Post by darkod on 2018-09-04
Does this help? [https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan](https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan)

You have examples there for multiple NICs and also for vlans.

---

### Post by ds-dv on 2018-09-04
> **darkod said:**
> Does this help? [https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan](https://blog.ubuntu.com/2017/12/01/ubuntu-bionic-netplan)

You have examples there for multiple NICs and also for vlans.

i read it a few days ago but couldnt figure out if the mac adresses they talked about are the ones of the NICs or just 'random' examples for clients
according to this i can directly link interfaces:
[https://netplan.io/examples](https://netplan.io/examples)

ill try again and report back :)

---

### Post by ds-dv on 2018-09-04
ok i got it to work with both nics.
the problem now is:
if i connect cable which on the switch is not vlan tagged to either of the interfaces everything works fine.

  if i connect a cable which on the switch is tagged with a vlan id to  either of the interfaces the box gets an IPaddress and gateway etc but  is not able to ping or reach any internet connection.

  same cable works with a windows 10 laptop prefektly fine.
  can someone help me fix it?

  
with kind regards

---

### Post by darkod on 2018-09-04
Can you post the content of the yaml file inside CODE tags? That should keep the formatting and make it easier to read.

Do you want to use vlan only on the primary NIC or on both?

---

### Post by ds-dv on 2018-09-04
> **darkod said:**
> Can you post the content of the yaml file inside CODE tags? That should keep the formatting and make it easier to read.

Do you want to use vlan only on the primary NIC or on both?

i edited so its no in code tags :)
with untagged vlan traffic it works fine.

so for now i will use untagged vlans...


now the last point i dont know how to fix is the splitting of the traffic.
How can i bind all lantraffic to NIC1 and force all Internettraffic to NIC2?

---

### Post by darkod on 2018-09-04
If all traffic (except LAN) has to go over NIC2, then set up the default gateway on NIC2.

The LAN traffic will usually be limited to one subnet only (the LAN subnet), so setting up static IP and netmask on NIC1 is enough to send LAN traffic over NIC1.

---

### Post by ds-dv on 2018-09-04
> **darkod said:**
> If all traffic (except LAN) has to go over NIC2, then set up the default gateway on NIC2.

The LAN traffic will usually be limited to one subnet only (the LAN subnet), so setting up static IP and netmask on NIC1 is enough to send LAN traffic over NIC1.

how do i set a default gateway?
my firewall makes a gateway for ervery vlan.

i have NIC1 dhcp  and NIC2 static (before i had both dhcp and let the firewall assign static ips)

---

