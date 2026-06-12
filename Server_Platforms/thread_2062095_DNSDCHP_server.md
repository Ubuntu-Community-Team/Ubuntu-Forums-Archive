---
title: "DNS/DCHP server"
date: 2012-09-24
forum: Server Platforms
---

### Post by Ram2012 on 2012-09-24
hi,
am trying to setup DNS/DCHP server in ubuntu 12.04 as in the link-  [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

I use network manager, so i installed dnsmasq-base, but not dnsmasq.

so i gave $ sudo /etc/init.d/dnsmasq-base restart 
command instead of $ sudo /etc/init.d/dnsmasq restart

i got an error "-bash: /etc/init.d/dnsmasq-base: No such file or directory", so how to restart my dns now.....

i also tried sudo /etc/init.d/dnsmasq restart

 * Restarting DNS forwarder and DHCP server dnsmasq                                                                                                                                                          
dnsmasq: failed to create listening socket for port 53: Address already in use
how to fix this...

---

### Post by xdracco on 2012-09-24
Personally, I found DNSMasq to be useful in certain environments but lately, I've been happy with ISC-DHCP-Server (aka DHCP-Server3). The developers of this DHCP server are the same as Bind9 so they would wonderful together. In fact, configuration files for both look quite similar which makes it somewhat easier. DNSMasq is a little on the weird side when it comes to it's configuration file. But it does work..

This set up is nice because you can dynamically pass dhcp client host names to Bind (much like a WINS server).

Anyways, since you're getting a port 53, port already in use, kill Bind first..

```
 $ /etc/init.d/bind9 stop
```and then start dnsmasq...

Basically DNSMasq wants to play DNS server while Bind is already running and listening to the default DNS port.

Hope that helps...

---

### Post by Ram2012 on 2012-09-25
hey thanks for the reply,

what is this nameserver,
```
/etc/resolv.conf file 
```

search yourisp.com
 nameserver 127.0.0.1
 nameserver 192.168.0.1 
nameserver 205.171.3.25 
nameserver 205.171.3.26

in the link he has specified to overwrite if not available, but in the conf file, it says to avoid hand written code

---

### Post by xdracco on 2012-09-25
/etc/resolv.conf is the file that the computer looks at to find out which DNS to query. It is generally OK to create/edit this file. I'm not sure why it says not to (mine does too) but I overwrote mine years ago and it's still the same.

I would continue with those directions. I wouldn't worry about the notice at the top of that file.

---

### Post by hhaydoura on 2012-09-27
sudo nano /etc/network/interfaces and sudo nano /etc/resolv.conf thats all what you need to edit to start the dns

---

### Post by d4m1r on 2012-09-28
1) DNSmasq is not installed by default on ubuntu server as it is part of network-manager (ubuntu desktop), but bind9 is.

2) If it is your first time setting up a DNS server, I'd go with bind9, especially because there is more documentation on it to help you set it up and troubleshoot.

---

