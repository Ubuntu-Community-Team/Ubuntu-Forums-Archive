---
title: "ubuntu server assign static ip"
date: 2018-04-17
forum: Server Platforms
---

### Post by am.steen on 2018-04-17
I fail comeletely to assign a static ip on ubuntu server
I try every thing

I intsall ubuntu server in network 172.30.3.0 with auto dhcp

I get my interface name from ifconfig - it was ens160

After finished installtion I go to interfaces file and find only this inside :
```
auto lo
iface lo inet loopback
```


So I add the following lines :-

```
iface ens160 inet static
address 172.30.3.60
netmask 255.255.255.0
network 172.30.3.0
broadcast 172.30.3.255
gateway 172.30.3.254
```

After restart and run ifconfig the server still get its auto ip 172.30.3.19

Also 
I edit the resolv.config file and add my dns but it back to its contents after restart

Please help

---

### Post by slickymaster on 2018-04-17
*Thread moved to **Server Platforms**.*

---

### Post by am.steen on 2018-04-17
Thanks for code fix 

But I still have the problem please help

---

### Post by am.steen on 2018-04-17
Sorry I forget my server is ubuntu 17.10

---

### Post by am.steen on 2018-04-17
Ok I found it Foor other who have same issu :-

Ubuntu 17.1 have another file for net work config

check this link 

[https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/](https://websiteforstudents.com/configuring-static-ips-ubuntu-17-10-servers/)

Sorry I do not know how to close this issue

---

