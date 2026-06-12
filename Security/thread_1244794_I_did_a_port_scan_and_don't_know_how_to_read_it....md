---
title: "I did a port scan and don't know how to read it..."
date: 2009-08-19
forum: Security
---

### Post by kibster on 2009-08-19
Could someone interrupt this for me please... I don't know what I'm looking at


Nmap Options: -p1-5000 -T4 -sS 24.56.204.131

Starting Nmap 4.75 ( [http://nmap.org](http://nmap.org) ) at 2009-08-20 02:28 St&#65533;edn&#65533; Evropa (letn&#65533; &#65533;as)
All 5000 scanned ports on c-24-56-204-131.customer are filtered

Nmap done: 1 IP address (1 host up) scanned in 710.65 seconds

---

### Post by Dave_Connor on 2009-08-19
This means there are no services running on your system. If you running something like ssh. Nmap would report back that port 22 is open on your LAN.

---

### Post by kibster on 2009-08-19
Hi Dave,

So I guess its a good report then.. Nothing bad ?

Thank you !

---

### Post by cariboo on 2009-08-20
If there had been any open ports, the output would have looked something like this:

```
Starting Nmap 5.00 ( http://nmap.org ) at 2009-08-19 21:19 PDT
Interesting ports on willy (192.168.1.250):
Not shown: 4992 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
631/tcp  open  ipp
3306/tcp open  mysql
MAC Address: 00:00:00:00:00:00 (D-Link)
```

I altered the mac address, because that is unique to each network adapter.

---

### Post by kibster on 2009-08-20
Oh ok... I know for linux users you have to be pretty savvy which I am not. One thing that attracted me to linux was that it was more secure than windows and you couldn't or shouldn't get any viruses ..windows was plagued  with them..and you were always getting hit on. so thats why I went linux...but I can hardly keep it going with all the new stuff that you have to know. 

Thanks for steering me in the right direction.

---

### Post by koenn on 2009-08-20
> **Dave_Connor said:**
> This means there are no services running on your system. If you running something like ssh. Nmap would report back that port 22 is open on your LAN.
not exactly : ports where no services are running, are reported as "closed".
"filtered" means that something is preventing nmap from connecting to the port - a firewall with "DROP" policies / rules, most likely. So nmap says 'filtered' because it assumes a packet filtering firewall is interfering with access to that port. 

> **kibster said:**
> 
So I guess its a good report then.. Nothing bad ?

yes, it's still a good report

---

### Post by kibster on 2009-08-20
Well thats a load off my mind... Thank you very much for the explanation. 

I don't know of these things. Every time my computer would be slow or do something odd I would think that I was under attack as I found out using windows .

Thank You very much..

Russell

---

