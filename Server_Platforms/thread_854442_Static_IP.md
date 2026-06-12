---
title: "Static IP"
date: 2008-07-09
forum: Server Platforms
---

### Post by waterrr on 2008-07-09
Hi,
How do I set up a static ip on a ubuntu server? (I'm using Ubuntu 6.06 LTS)
Thanks

---

### Post by osjak on 2008-07-09
In the file /etc/network/interfaces
replace
```
auto eth0
iface eth0 inet dhcp
```
with this:
```
auto eth0
iface eth0 inet static
address **192.168.1.100**
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```
where 192.168.1.100 is your static IP.

Then restart the network service:
```
sudo /etc/init.d/networking restart
```

---

### Post by waterrr on 2008-07-09
please read pm

---

### Post by waterrr on 2008-07-09
I just chnged the following codes that youve stated and when i went to restart it, i got this result

*Reconfiguring network interfaces...
SIOCADDRT: Network is unreachable
Failed to bring up eth0.

---

### Post by osjak on 2008-07-09
What is your router internal IP. In my example it is 192.168.1.1, and the network is 192.168.1.0. you may have it set up at 192.168.0.0 or something else.

If you still get an error, return 
```
auto eth0
iface eth0 inet dhcp
```
back, restart the network and see what settings you get from DHCP:
```
sudo ifconfig
```

Then just adjust the numbers accordingly. Sorry for saying it now and not in my first post.

---

