---
title: "[SOLVED] can't blacklist ipv6 in gutsy server?"
date: 2007-11-01
forum: Server Platforms
---

### Post by ruibernardo on 2007-11-01
Hi,

I've just upgraded my Feisty server to Gutsy. Back in Feisty I've blacklisted the ipv6 module in /etc/modprobe.d/blacklist and it's still there, but now on Gutsy, when I type lsmod|grep ipv6:

```
 user@server:~$ lsmod|grep ipv6
** ipv6**                  278916  24 nf_conntrack_h323
```and with ifconfig:

```
 eth0      Link encap:Ethernet  HWaddr --:--:--:--:--:--  
          inet addr:--.---.---.---  Bcast:--.---.---.---  Mask:---.---.---.---
          **inet6 addr: ----::---:----:----:----/-- Scope:Link**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33025 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12017296 (11.4 MB)  TX bytes:8432092 (8.0 MB)
          Interrupt:10 Base address:0xc100
```Netstat also outputs tcp6 connections.

How do I disable ipv6 in Gutsy?

---

### Post by ruibernardo on 2007-11-02
The nf_conntrack_h323 module was the queue. It was used by nf_nat_h323. 

I've started wondering why those modules were being loaded since I didn't even had a module file on my shorewall configuration and I didn't have any SIP/H323 protocol applications installed or working on my Gutsy server.

The problem was that I didn't have a module file in shorewall configuration directory and shorewall/iptables was loading all the modules, _*even with "blacklist ipv6" in the file /etc/modprobe.d/blacklist!!*_ So I've created and empty module file in /etc/shorewall/ and the problem was solved, but that was not happening in Feisty. Ipv6 wasn't being loaded in Feisty with the same (absent shorewall module file) configuration, so I find this issue a little bit strange. 

Did this happen to anybody else? Should I fill a bug in Launchpad about /etc/modprobe.d/blacklist not working for ipv6 in the Gutsy kernel?

---

### Post by cerbero on 2007-11-02
Hi. I'm having this exact problem too. Could you please explain in more detail what you did to get around it? I haven't had much experience with module management, so I'm not sure how to "create an empty module file", specifically. Thanks!

---

### Post by ruibernardo on 2007-11-02
> **cerbero said:**
> Hi. I'm having this exact problem too. Could you please explain in more detail what you did to get around it? I haven't had much experience with module management, so I'm not sure how to "create an empty module file", specifically. Thanks!

I've copied the /usr/share/doc/shorewall/default-config/modules to /etc/shorewall, edited it, deleted all the lines with modules in it (I don't need any of them here) but the comments in the beginning and the last line (just comments, as if it was empty), then I rebooted the server.

That way shorewall will not load any iptables module, specifically nf_nat_h323 and nf_conntrack_h323, the ones that were loading ipv6, and will not load ipv6 since it is (it was here) blacklisted in /etc/modprobe.d/blacklist.

More simple: copy the file /usr/share/doc/shorewall/default-config/modules to /etc/shorewall, remove nf_nat_h323 and nf_conntrack_h323, blacklist ipv6 in /etc/modprobe.d/blacklist and reboot.

I just don't understand why was ipv6 being loaded in the first place since it was blacklisted...

---

### Post by cerbero on 2007-11-03
That worked wonders. Thanks for your help!

---

