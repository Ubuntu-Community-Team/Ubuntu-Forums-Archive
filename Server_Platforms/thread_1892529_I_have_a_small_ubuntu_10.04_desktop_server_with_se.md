---
title: "I have a small ubuntu 10.04 desktop server with several 100 different ip hits."
date: 2011-12-08
forum: Server Platforms
---

### Post by jaho22 on 2011-12-08
I have a small desktop server with several 100's of different ip hits.

I want to protect from bruteforce attacks and worms and trojans, and from everyone who try to take my server to under theyre own control, is there anything else i should know ?

--

Ubuntu is quite a nice.

---

### Post by SlugSlug on 2011-12-08
for ssh attacks look at denyhosts

for email server, ftp etc lok at fail2ban

I run both

---

### Post by elico on 2011-12-08
simple iptables rule to limit the max connection to 3 per sec will give you a lot.
but you should ask yourself what is the hit intention.
is it for specific purpose or other matter.
it might be an attack but can also be a mistake on a dns resolution.

---

### Post by Habitual on 2011-12-08
> **elico said:**
> ...but can also be a mistake on a dns resolution.

+1

Terminal > 
```
sudo zgrep ipa.ddr.ess /var/log/*
```

---

### Post by SlugSlug on 2011-12-08
```
sudo grep Failed /var/log/auth.log
```

---

