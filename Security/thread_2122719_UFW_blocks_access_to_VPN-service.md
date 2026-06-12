---
title: "UFW blocks access to VPN-service"
date: 2013-03-06
forum: Security
---

### Post by Askel on 2013-03-06
Hello

I can't connect to my VPN-service (Anonine) without turning of UFW. From what I can gather port 1723 needs to be open, but even when I added that rule to UFW it still blocks connection to the VPN. I can only connect to it if I turn of UFW. I use PPTP.

//Askel

---

### Post by carl4926 on 2013-03-06
If you are behind a hardware firewall? Do you really need the software firewall?

---

### Post by Askel on 2013-03-06
Well I really don't know. I'm kind of new to the sercurityissue in ubuntu. So you're saing I don't need UFW if I use VPN? But I still would like it to work with the firewall enabled. If not for any other reason than to learn how to fix the problem.

//Askel

---

### Post by Askel on 2013-03-07
I found this thread and solved it, so now it works fine.
[http://ubuntuforums.org/showthread.php?t=1113911](http://ubuntuforums.org/showthread.php?t=1113911)

> **Askel said:**
> Well I really don't know. I'm kind of new to the sercurityissue in ubuntu. So you're saing I don't need UFW if I use VPN? But I still would like it to work with the firewall enabled. If not for any other reason than to learn how to fix the problem.

//Askel

---

