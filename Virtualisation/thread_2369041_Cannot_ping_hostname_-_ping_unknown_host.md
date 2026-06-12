---
title: "Cannot ping hostname - ping: unknown host"
date: 2017-08-17
forum: Virtualisation
---

### Post by nomagon on 2017-08-17
Hi,

Somehow I've lost the ability to ping my computer by its hostname.  

happy@happy-VirtualBox:~$ hostname
happy-VirtualBox
happy@happy-VirtualBox:~$ ping happy-VirtualBox
ping: unknown host happy-VirtualBox
happy@happy-VirtualBox:~$ 

Any ideas?

Thanks!

---

### Post by wildmanne39 on 2017-08-17
*Thread moved to **Virtualisation**.*

---

### Post by nomagon on 2017-08-18
Thanks, after following those steps in that link, still no go, unable to ping my computer hostname.

---

### Post by deadflowr on 2017-08-18
> **nomagon said:**
> Thanks, after following those steps in that link, still no go, unable to ping my computer hostname.

What link?

Also, what does the /etc/hosts file show?

---

### Post by nomagon on 2017-08-18
127.0.0.1       localhost
127.0.1.1       happy-VirtualBox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters


If i do... sudo ping happy-VirtualBox i can ping successfully.  Just ping happy-VirtualBox yeilds unknown host.

---

### Post by mrsteffenjo on 2017-11-06
Both of these files should probably be 644:
```
stat -c "%a %n" /etc/nsswitch.conf
stat -c "%a %n" /etc/hosts
```

This command should probably fix your issue:
```
sudo chmod 644 /etc/hosts
```

---

