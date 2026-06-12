---
title: "recommended port scanner to help with security risks"
date: 2008-12-22
forum: Security
---

### Post by pshootr on 2008-12-22
I was wanting to do a port scan on my local network. I would like to run the scanner on a windows machine and scan the ip of my ubuntu server. Can some one suggest a scanner for me?

---

### Post by tubasoldier on 2008-12-22
If you are just looking to scan ports then check out nmap found at insecure.org

---

### Post by pshootr on 2008-12-22
> **tubasoldier said:**
> If you are just looking to scan ports then check out nmap found at insecure.org

Thanks for the tip. I did notice nmap in a search, but is seemed to need some dependencies in order to run on windows. I just want a simple port scanner that will run on windows without any dependencies.

---

### Post by Vantrax on 2008-12-22
ethereal might help but nmap really is the way to go.

---

### Post by jpkotta on 2008-12-22
[http://nmap.org/book/inst-windows.html](http://nmap.org/book/inst-windows.html)

---

### Post by Sarmacid on 2008-12-22
You'd probably prefer zenmap, which is just a graphical front end for nmap.

---

### Post by cdenley on 2008-12-22
Why port scan your ubuntu computer when you can easily see all listening processes?
```

sudo netstat -tulnp

```
This way you can see not only what ports you're listening on (tcp or udp) without checking every single port, but it also tells you which process is listening on which port.

---

### Post by pshootr on 2008-12-22
> **cdenley said:**
> Why port scan your ubuntu computer when you can easily see all listening processes?
```

sudo netstat -tulnp

```
This way you can see not only what ports you're listening on (tcp or udp) without checking every single port, but it also tells you which process is listening on which port.

Good point. Thanks for the useful information. I will try it out. Also thanks to all who have responded with suggestions.

---

### Post by rweaver on 2008-12-23
> **pshootr said:**
> Good point. Thanks for the useful information. I will try it out. Also thanks to all who have responded with suggestions.

The windows port of nmap and netcat are both good also if you end up needing an actual port scanner.  Both have good binary distributions you can use.

---

### Post by erwall on 2008-12-23
I can't believe no one has mentioned nessus!  It does way more than simple port scanning, it will tell you specific vulnerabilities and most of the time tell you how to fix them.

---

### Post by Sarmacid on 2008-12-24
> **erwall said:**
> I can't believe no one has mentioned nessus!  It does way more than simple port scanning, it will tell you specific vulnerabilities and most of the time tell you how to fix them.
Yes, Nessus does a lot more than nmap, but nmap is so much simpler.

---

