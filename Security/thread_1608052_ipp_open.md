---
title: "ipp open"
date: 2010-10-28
forum: Security
---

### Post by ubudog on 2010-10-28
Hi there!  I ran an nmap scan on myself using:
```
nmap localhost
```

And it showed "ipp" as being open.  What is this and how do I close it?

---

### Post by anomie on 2010-10-28
Running nmap against localhost is not particularly useful. More enlightening output can be had from: 
**# netstat -ltnp**

(i.e. Show only listening tcp ports, don't resolve IPs/port assignments, and also show the associated PID/program name.) 

If it's listening only on localhost, then you're good. The IPP listener you're seeing is probably cupsd, BTW.

---

### Post by ubudog on 2010-10-28
> **anomie said:**
> Running nmap against localhost is not particularly useful. More enlightening output can be had from: 
**# netstat -ltnp**

(i.e. Show only listening tcp ports, don't resolve IPs/port assignments, and also show the associated PID/program name.) 

If it's listening only on localhost, then you're good. The IPP listener you're seeing is probably cupsd, BTW.

Thanks. :)

---

