---
title: "Access VirtualBox guest from firefox host"
date: 2012-09-12
forum: Virtualisation
---

### Post by mrwebmaster on 2012-09-12
Hi,

I have an Ubuntu 12.04 server machine on Virtualbox , hosted on Xubuntu 12.04 .

I'm trying to access Apache from Firefox. I tried following:

On host:
>ifconfig 

> inet addr: 10.0.2.15On Virtualbox: 
file > preferences > network > new host-only network 
ipv4adress is: 192.168.56.1
on the machine, settings > network > adapter 2 > "Host-only adapter" 

On Xubuntu host:
>sudo nano /etc/hosts
10.0.2.15 example.local

In Firefox, I try to go to "10.0.2.15", and after some time, I get a "Server not found".  I tried also "http://192.168.56.1" and "example.local"

I tried also: 
on the machine, settings > network > adapter 2 > "Bridged adapter" (eth0). 

I disabled firewall on both host and guest using: 

$ sudo iptables -X
 $ sudo iptables -t nat -F
 $ sudo iptables -t nat -X
 $ sudo iptables -t mangle -F
 $ sudo iptables -t mangle -X
 $ sudo iptables -P INPUT ACCEPT
 $ sudo iptables -P FORWARD ACCEPT
 $ sudo iptables -P OUTPUT ACCEPT

and

$ sudo ufw disable 

I can access Internet from host and guest. 

Thanks for your help!

---

### Post by CharlesA on 2012-09-13
Just set the network adapter to bridged and access it via the IP the guest gets.

---

### Post by mrwebmaster on 2012-09-13
Thanks, I've already tried that

settings > network > adapter 2 > "Bridged adapter" (eth0).

---

### Post by CharlesA on 2012-09-13
Check ifconfig again, a 10.0.2.15 IP is associated with NAT, not bridged.

---

### Post by mrwebmaster on 2012-09-21
Thanks, it's working now. The trick was putting the bridged in the first position, and NAT in the second.

---

