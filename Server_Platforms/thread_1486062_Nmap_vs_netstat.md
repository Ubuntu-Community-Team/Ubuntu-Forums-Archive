---
title: "Nmap vs netstat"
date: 2010-05-17
forum: Server Platforms
---

### Post by awacs on 2010-05-17
In conjunction with another question, I noticed on this new Karmic installation, that nmap gives different results from netstat:

# nmap localhost   #same results by IP
[...]
21/tcp  open  ftp
22/tcp  open  ssh
23/tcp  open  telnet
25/tcp  open  smtp
53/tcp  open  domain
110/tcp open  pop3
139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
631/tcp open  ipp

but,

# netstat -aunt|grep LISTEN # right side truncated for clarity
[...]
tcp        0      0 0.0.0.0:445             
tcp        0      0 127.0.0.1:10023         
tcp        0      0 0.0.0.0:139             
tcp        0      0 0.0.0.0:110             
tcp        0      0 0.0.0.0:4559            
tcp        0      0 216.254.79.127:53       
tcp        0      0 10.1.1.1:53             
tcp        0      0 127.0.0.1:53            
tcp        0      0 0.0.0.0:21              
tcp        0      0 0.0.0.0:22              
tcp        0      0 0.0.0.0:631             
tcp        0      0 0.0.0.0:23              
tcp        0      0 127.0.0.1:953           
tcp        0      0 0.0.0.0:25              
tcp6       0      0 :::22                   
tcp6       0      0 :::631                  

Thus several ports, 10023, 4559, 953 and 39804
don't show on nmap, but they're really open.

Anyone know why?

Thanks!

---

### Post by cdenley on 2010-05-17
Nmap checks commonly used ports to see if they are open. It does not check all 65,535 possible ports.

---

### Post by awacs on 2010-05-17
> **cdenley said:**
> Nmap checks commonly used ports to see if they are open. It does not check all 65,535 possible ports.

Oh. Then why does it say, above the listing: "Not shown: 991 closed ports", as if it checked (at least) the first thousand?

Let's see if you're right:

# nmap localhost |grep 953
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
# nmap localhost -p 953

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-05-17 15:26 EDT
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on pizza (127.0.0.1):
PORT    STATE SERVICE
953/tcp open  rndc

Well, I'll be.. That was it. Interesting. 

Thanks for that lesson!

---

### Post by cdenley on 2010-05-17
> **awacs said:**
> Oh. Then why does it say, above the listing: "Not shown: 991 closed ports", as if it checked (at least) the first thousand?


It may have checked a thousand, but it didn't check the first thousand, and it didn't check all 65,535. It checked the most common ones, many of which are over 1000, like 5900 or 3389. You can specify a port range for nmap if you want.

---

