---
title: "Static IP or DNS Name"
date: 2010-11-27
forum: Server Platforms
---

### Post by jymere on 2010-11-27
Hi.

I have installed a ssh server on a computer (Ubuntu 10.04). This computer will be reboot many times, so the IP address is going to change. As a result, I couldn't connect with an other computer on this server via ssh.
That's why I search a solution: either I assign a static IP on my server computer or I heard that I could use a dns name.  I don't know if the latter solution is good so I hope to have some precisions. 
Also, I tried to have a static IP by editing the file : /etc/network/interfaces but it doesn't work.

How can I do ?

Thanks.

---

### Post by windependence on 2010-11-27
Find the section in your /etc/network/interfaces file and make it look similar to this but use your own IP address:
 
```
 
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1

```
 
Then restart the network (if you don't do this it won't work).
 
```
 
sudo /etc/init.d/networking restart

```
 
Why are you rebooting a Linux server? There shoulod be almost no reason to ever have to reboot.
 
-Tim

---

### Post by jymere on 2010-11-27
re,

ok it's working a bit ...
in fact, my ip address is static and i can connect me via ssh to the server with an other computer.
However, my server can't connect to internet ( command ping tested ).

I just changed the ip address. Do I have to change gateway and broadcast (what is the use of this two addresses ?).

also, it's a ssh connection between two personal computer and both of them are going to be shutdown. I just need this connection temporarily.

---

### Post by windependence on 2010-11-27
You'll need a gateway address (usually the address of your router) but the broadcast is not necessary. The missing gateway address is why you can't acces the internet.
 
-Tim

---

### Post by jymere on 2010-11-27
ok thanks a lot it's works.

@+

---

### Post by windependence on 2010-11-27
You're welcome :-)
 
-Tim

---

