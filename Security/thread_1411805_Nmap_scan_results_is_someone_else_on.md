---
title: "Nmap scan results is someone else on?"
date: 2010-02-20
forum: Security
---

### Post by vdubhack on 2010-02-20
I did just a basic nmap scan of my entire network at home last night because of sheer boredom I ran this scan  ```
 nmap 192.168.0.0/16 
``` it showed the three devices that I was expecting but then it stated listing others that I know are not any of my devices.The results I got that dont make sense are below.  ```
 Interesting ports on 192.168.9.252: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy  Interesting ports on 192.168.9.253: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy  Interesting ports on 192.168.10.252: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy  Interesting ports on 192.168.10.253: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy  Interesting ports on 192.168.11.252: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy  Interesting ports on 192.168.11.253: Not shown: 998 filtered ports PORT     STATE SERVICE 80/tcp   open  http 8080/tcp open  http-proxy 
``` Does this mean these are others connected to my network or is this something else? Or could these have to do with say my modem and router? I saw proxy so it made me think that these might all be outside connections using a proxy to get into my network. So with all that rambling can anyone make sense of why those showed up. Also if you need more info please feel free to let me know what you need.   Thanks for you help

---

### Post by thewanderer on 2010-02-22
Try:
> nmap -PN -A -sV 192.168.0.0/16

This will give you more info to work with.

Could it be that there is only two hosts showing up but each is configured with 3 IP's.

---

### Post by cariboo on 2010-02-22
That almost looks like you may be seeing systems on your isp's internal network.

---

### Post by d3v1150m471c on 2010-02-22
> **cariboo907 said:**
> That almost looks like you may be seeing systems on your isp's internal network.

Exactly. If that 192.blah.blah.252 wasn't your IP address then nmap is showing services running on someone's computer that happens to be on your ISP network.

---

