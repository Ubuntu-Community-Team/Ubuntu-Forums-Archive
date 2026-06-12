---
title: "Configure ufw to drop icmp echo requests?"
date: 2010-07-12
forum: Security
---

### Post by Seanlol on 2010-07-12
I've been trying to configure ufw to drop ping requests for a couple days now, and I can't figure it out. I've tried a couple different methods in some different guides, still nothing. Anyone know how to do this?

---

### Post by FuturePilot on 2010-07-12
In /etc/ufw/before.rules change 
```
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```
to
```
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
```

Then restart UFW.

```
sudo restart ufw
```

---

### Post by Seanlol on 2010-07-13
> **FuturePilot said:**
> In /etc/ufw/before.rules change 
```
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
```to
```
-A ufw-before-input -p icmp --icmp-type echo-request -j DROP
```Then restart UFW.

```
sudo restart ufw
```

I did this. The computer is still accepting ping requests.

---

### Post by bodhi.zazen on 2010-07-13
> **Seanlol said:**
> I did this. The computer is still accepting ping requests.

Accepts ping requests from where ? localhost ? you LAN ?

Do you have any additional rules that accept connections earlier in your rule set ?

Post ```
sudo ufw status verbose
sudo iptables -L -v -n
```

---

### Post by mondo1287 on 2010-11-04
Note that after modifying /etc/ufw/before.rules you have to do:
> ufw disable
ufw enable

---

