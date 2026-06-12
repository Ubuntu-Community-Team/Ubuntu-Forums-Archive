---
title: "nmap scan"
date: 2011-06-03
forum: Security
---

### Post by spiky001 on 2011-06-03
I have just scanned my external ip with nmap -sO external ip  results were```
  1        open          icmp,  2        open|filtered igmp,  6        open          tcp,  17       open          udp,  47       open|filtered gre,  103      open|filtered pim,  136      open|filtered udplite,  255      open|filtered unknown,
```    Can I take it these ports are to do with nmap scan? I also ran the same scan with nmap online result was different, ```
 1        open          icmp
```

---

### Post by dodo3773 on 2011-06-04
> **spiky001 said:**
> I have just scanned my external ip with nmap -sO external ip  results were```
  1        open          icmp,  2        open|filtered igmp,  6        open          tcp,  17       open          udp,  47       open|filtered gre,  103      open|filtered pim,  136      open|filtered udplite,  255      open|filtered unknown,
```    Can I take it these ports are to do with nmap scan? I also ran the same scan with nmap online result was different, ```
 1        open          icmp
```

Are you just trying to find out what ports are open on your computer and / or router? If so, there is no need to scan your external ip address. Also, as far as I know, nmap does not open ports when it does a scan. I am not even sure if that is possible. It scans the network and finds ports that are already open.

---

### Post by spiky001 on 2011-06-04
Hi I would like to know what these open ports are. I dont seem to remember them being open before but it has been awhile since I ran a scan, it is also the 1st time I ran this scan, I was just being curious at different options of nmap, When I got back results I did wonder why all open I have ssh open on lan nothing to outside (looks like i,m wrong). Also how come nmap online got different results with same scan options?

---

### Post by dodo3773 on 2011-06-04
> **spiky001 said:**
> Hi I would like to know what these open ports are. I dont seem to remember them being open before but it has been awhile since I ran a scan, it is also the 1st time I ran this scan, I was just being curious at different options of nmap, When I got back results I did wonder why all open I have ssh open on lan nothing to outside (looks like i,m wrong). Also how come nmap online got different results with same scan options?

Scan your router and your computer on your lan to find open ports.
Scan your network like this

```

sudo nmap -T4 -PN -A -v 192.168.1.0-255

```

Unless your router is 192.168.0.1 
If that is the case change the above accordingly.


Then look at the results. To find out which ip address is yours on your lan run

```
ifconfig
```

This should tell you what ports are open.

---

### Post by dodo3773 on 2011-06-04
Also, see this

[http://www.iana.org/assignments/port-numbers](http://www.iana.org/assignments/port-numbers)

for the port numbers.

---

### Post by crispy_420 on 2011-06-07
icmp is just ping. Does your router/firewall have the option to disable ping on WAN port?

---

