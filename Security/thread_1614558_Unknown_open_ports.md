---
title: "Unknown open ports"
date: 2010-11-05
forum: Security
---

### Post by bouncingwilf on 2010-11-05
While (attempting) to set up ssh on a couple of machines (not this one)  I've noticed that I keep getting some strange unknown ports showing as open on my PC when I do a port scan on its address. They are only opened transiently, they are all high numbers  eg 33348, 41147, 50370 etc.

I Have opened no ports on this machine at any time and ufw is set to deny all incoming. Do I need to look further?


Bouncingwilf

---

### Post by brian_p on 2010-11-05
> **bouncingwilf said:**
> 

I Have opened no ports on this machine at any time and ufw is set to deny all incoming. Do I need to look further


Not necessarily. They'll be connections you have initiated. Possibly browser connected. 

```
netstat -tulpan
```

might interest you.

---

### Post by cariboo on 2010-11-05
If you are using the portscan tool from the Network Tools menu item, you could be getting false positives. I've been waiting for over 2 years for upstream to fix this problem.

I would suggest using nmap and if you need a gui for it, zenmap, to do your portscans.

---

### Post by bouncingwilf on 2010-11-06
Many thanks - ports do indeed appear to be browser related + weather applet + cupsd - but I shall keep an eye on things.

Bouncingwilf

---

