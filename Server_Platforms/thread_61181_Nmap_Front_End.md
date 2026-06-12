---
title: "Nmap Front End"
date: 2005-08-30
forum: Server Platforms
---

### Post by fartbarker on 2005-08-30
25/tcp open smtp
631/tcp open ipp

Is this normal? How do I and/or should I close them?

btw this was done on 127.0.0.1 
another scan on my machine ip address said all ports were closed  :?

---

### Post by AgenT on 2005-08-30
While this may be wrong, the ports you see open are opened for localhost only so they are technically not really "open". This would the reason why you would get all ports being closed if you did a scan from a computer on your lan.

---

### Post by fartbarker on 2005-08-30
thx

---

### Post by Spudgun on 2005-09-02
Aye, use the 'Shields Up' test to scan your PC from the outside.

---

### Post by bionnaki on 2005-09-02
how reliable is sheilds up, btw?

---

### Post by Spudgun on 2005-09-03
Very, I'd say. I've had no problems with it, and always use it to test out my firewall rules.

---

