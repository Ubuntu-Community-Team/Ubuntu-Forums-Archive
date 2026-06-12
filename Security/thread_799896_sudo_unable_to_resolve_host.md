---
title: "sudo: unable to resolve host"
date: 2008-05-19
forum: Security
---

### Post by whoop on 2008-05-19
All of a sudden when I use the sudo command I get the following line:
sudo: unable to resolve host whoop-desktop

what does this mean and what can I do about it ?

---

### Post by Monicker on 2008-05-19
Please read this sticky thread:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by whoop on 2008-05-19
I fixed it myself. I remembered that I had been messing with my domain name in network settings

---

### Post by whoop on 2008-05-19
thanks, Monicker. Guess I was sleeping on the job

---

### Post by The Cog on 2008-05-19
Yup. If you change the hostname in /etc/hostname, you must also fix up /etc/hosts so the new name resolves to 127.0.0.1. The safest way is to edit hosts and add the new name, then edit hostname, then go back to hosts to remove the old hstname.

---

### Post by linuxNewb on 2011-10-04
The Cog, I think you meant 127.0.1.1

---

### Post by capscrew on 2011-10-04
> **The Cog said:**
> Yup. If you change the hostname in /etc/hostname, you must also fix up /etc/hosts so the new name resolves to 127.0.0.1. The safest way is to edit hosts and add the new name, then edit hostname, then go back to hosts to remove the old hstname.

I think you misspoke there.  The hostname has to resolve to **an** interface on the host (any). This allows you to communicate with the host using...the host name. My desktop host (malibu) resolves to 192.168.1.3.```
/etc/hosts
127.0.0.1	localhost
192.168.1.3	malibu surfrider
```

---

### Post by capscrew on 2011-10-04
> **linuxNewb said:**
> The Cog, I think you meant 127.0.1.1
Using 127.0.1.1 is due to a Debian bug.  The IP 127.0.0.1 and 127.0.1.1 both resolve to the loopback address.

---

### Post by CharlesA on 2011-10-04
Back to sleep thread..

---

