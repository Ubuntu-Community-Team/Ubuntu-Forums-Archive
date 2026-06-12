---
title: "Can't connect to Ubuntu 14.04 from outside of VirtualBox"
date: 2016-09-28
forum: Virtualisation
---

### Post by thoan001 on 2016-09-28
I'm trying to complete this project in a minimal install of Ubuntu 14.04. I'm absolutely new to VirtualBox and Ubuntu, so I don't know much of what I'm doing yet.
So far, I've installed it, set up Adapter 1 in VirtualBox to Host Only, Adapter 2 to NAT and set the portforward to 22, set /etc/network/interfaces to:
```

#Loopback
auto lo
iface lo inet loopback

#Primary
auto eth0
iface eth0 inet static
address 192.168.56.20
netmask 255.255.255.0
network 192.168.56.0
broadcast 192.168.56.255

#NAT
auto eth1
iface eth1 inet dhcp

```

I've also installed OpenSSH and PuTTY on it, and have enabled port 22 SSH, loopback, and HTML through IPTables. The main problem being, PuTTY keeps timing out and won't connect to it, same with pinging it from cmd. (Locally)
Inside of the VM Ubuntu it can successfully ping google and it can connect to its own SSH. Outside of it I can't connect...
Any help would be appreciated.

---

### Post by howefield on 2016-09-28
Thread moved to the ""*Virtualisation* forum.

---

### Post by SeijiSensei on 2016-09-28
Configure the primary interface as "bridged."  That will give it an IP address on the same network as the host making it visible to all the other machines on the network.

---

### Post by thoan001 on 2016-09-28
I've just now set it to bridged and it seems to work...but I still can't seem to connect to it with PuTTY with the IP 192.168.56.20 on port 22.
Is there anything else I should try? Also thanks for the fast reply!

---

### Post by thoan001 on 2016-09-28
I actually just figured it out somehow: I changed the port forwarding part on the NAT connection portforwarding to have this:
Host IP: 127.0.0.1, Port: 22, Guest IP: 10.3.15, Guest port 22
and then I connected to PuTTY using 127.0.0.1.
Thanks for the help!

---

