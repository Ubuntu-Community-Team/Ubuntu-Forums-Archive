---
title: "Apache Hates Me"
date: 2006-06-26
forum: Server Platforms
---

### Post by Jayzilla on 2006-06-26
I set up an Apache server, and I can see my index page just fine on every box on my network...but nobody outside of my network can reach it.  I'm behind a router, so I set up port forwarding on ports 80 and 443...it still doesn't work.  Any idea what's going on here?

---

### Post by scxtt on 2006-06-26
firewall?

---

### Post by Jayzilla on 2006-06-26
It's disabled.

---

### Post by scxtt on 2006-06-26
i'm stumped, i installed apache2 / php5 yesterday on a Xubuntu VM and all i had to do was forward port 80 to its IP ... i could get to it fine from work ...

---

### Post by LordHunter317 on 2006-06-26
What does ports.conf say?

Are you sure you enabled forwarding correctly?

---

### Post by Jayzilla on 2006-06-26
/etc/cups/cups.d/ports.conf reads:

```
Listen localhost:631
Listen /var/run/cups/cups.sock
```

---

### Post by scxtt on 2006-06-26
```
scxtt@vm$host:~$ cat /etc/apache2/ports.conf
Listen 80
```i think that's the wrong "ports.conf" -- i have a cups one also on my box that doesn't have apache2 installed (the VMware host) ...

---

