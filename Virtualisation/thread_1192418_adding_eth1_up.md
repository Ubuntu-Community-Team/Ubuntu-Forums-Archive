---
title: "adding eth1 up"
date: 2009-06-20
forum: Virtualisation
---

### Post by siddukirk on 2009-06-20
Hi all,
I am installing a virtualization software on my Ubuntu Hardy 8.04 
at one point the install doc says the following in bold  which i am not sure what it is ?
# Add internet connectivity (eth1) for the guests (tap0). Do NOT add eth0
# to the bridge or your host will be disconnected from the LAN...
sudo ifconfig eth1 up
sudo ifconfig eth1 promisc
but when i try to the run the following command it results in error as No such device found 
siddu@siddu-desktop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

how can i bring the eth1 up and my /etc/network/interfaces say the following 
siddu@siddu-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

Please Any inputs are welcome

---

### Post by cariboo on 2009-06-22
Moved to virtuaalization

---

### Post by bodhi.zazen on 2009-06-23
> **siddukirk said:**
> Hi all,
I am installing a virtualization software on my Ubuntu Hardy 8.04 
at one point the install doc says the following in bold  which i am not sure what it is ?
# Add internet connectivity (eth1) for the guests (tap0). Do NOT add eth0
# to the bridge or your host will be disconnected from the LAN...
sudo ifconfig eth1 up
sudo ifconfig eth1 promisc
but when i try to the run the following command it results in error as No such device found 
siddu@siddu-desktop:~$ sudo ifconfig eth1 up
eth1: ERROR while getting interface flags: No such device

how can i bring the eth1 up and my /etc/network/interfaces say the following 
siddu@siddu-desktop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

Please Any inputs are welcome

[http://blog.bodhizazen.net/linux/kvm_network_scripts/](http://blog.bodhizazen.net/linux/kvm_network_scripts/)

---

