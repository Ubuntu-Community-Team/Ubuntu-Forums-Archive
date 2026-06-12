---
title: "Security of my system."
date: 2008-08-12
forum: Security
---

### Post by Dave_Connor on 2008-08-12
With my system I am blocking off ssh attackers with denyhosts, I monitor my logs very often, I am using moblock with deluge blocklists. I have denyhosts.conf to block for http with my domain name. I checked my login logs and nothing seems suspicious. I was wondering, I didn't get any attacks today as I did with 4 yesterday, are these just at random or is denyhosts blocking the attacking ip ?

---

### Post by mrsteveman1 on 2008-08-12
Well, does denyhosts block by putting entries in hosts.deny or does it use iptables rules? Firewall events usually show up in dmesg or /var/log/messages.

The attacks are in fact random, on a server I manage for someone I see attacks all the time but they come in waves, there will be an hour or more of alphabetical SSH attempts, then nothing, then a few random attempts for root, then nothing, then more structured long term brute forcing.

I don't have an ubuntu system sitting here, but in CENTOS there is a specific log for auth failures of most types, /var/log/secure, that might tell you something if ubuntu has one too.

---

### Post by Dave_Connor on 2008-08-13
Denyhosts autologs the failed attempts into hosts.deny, I think Moblock handles the Iptables rules. There isn't any /var/log/secure. I'll look for an sshd log.

---

### Post by jerome1232 on 2008-08-13
this should get the logs for you
```
sudo grep sshd /var/log/auth.log | less
```It's pretty standard for denyhosts to block 1-4 ip's a day for me.

---

### Post by Dave_Connor on 2008-08-13
I checked the sshd of auth.log and the last sshd attack was 2 day ago and I did get refused connection from the same ip. I guess denyhosts log the guys IP and didn't let him connect and now gave up.

---

