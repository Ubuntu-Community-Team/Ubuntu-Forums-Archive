---
title: "Setting up Ubuntu 20 as modem/router for my home LAN"
date: 2021-01-19
forum: Server Platforms
---

### Post by wp.rauchholz on 2021-01-19
I hopefully have time this weekend to start working in this project. I come from Centos 7 and move to Ubunto becasue redhat killed the Centos idea of community based working
This is what I plan to to using firewalld and Ubuntu networmanager:
Set ISP router into bridge mode
internal NIC enp3so: static IP
...
dhcp4: no
      addresses:
        - 192.168.121.221/24
      gateway4: 192.168.121.1
      nameservers:
          addresses: [8.8.8.8, 1.1.1.1]

External NIC enp5s0)
How do I need to setup enp5s0? This has no IP (BOOTPROTO=none) and is the parent to ppp0

ppp0
sudo nmcli connection add type pppoe \
     ifname enp5s0 con-name ppp0 autoconnect true \
     username <pppoe_username> password <pppoe_password>

enable masquerading
sudo firewall-cmd --zone=public --add-masquerade --permanent

sysctl -w net.ipv4.ip_forward=1

Should this setup a basic working router or am I something missing?

Thank you

---

### Post by guiverc on 2021-01-19
It might help if you clarify your release of Ubuntu (there is no Ubuntu 20).

Ubuntu's main releases are *year.month* in format, eg. Ubuntu 20.04 LTS.  These releases use *deb* packages by default (but can use *snap* and other packages too), some have a shorter 9 months of life, and LTS releases have 5 years of support (which can be extended via ESM).

Ubuntu also has releases using the *year* format, eg. Ubuntu Core 20.  These releases use *snap* packages only, have 10 years of supported life (no mention is made of LTS; they've all longer supported lives than LTS for the main releases).  They are generally less powerful, but are also smaller making them ideal for their intended use inside devices, appliances and cloud infrastructure.  By default they have no GUI as headless use is expected, but can have a GUI added as well (GNOME is packaged as a *snap* for example).

Ubuntu 20 may mean a Ubuntu Core 20 system?   Is that what you mean?

---

