---
title: "Prelude-IDS and Ubuntu 8.10"
date: 2008-12-22
forum: Security
---

### Post by max_at_app on 2008-12-22
Hi, yesterday I tried to configure an IDS on my Ubuntu 8.10. I get inspiration from this tut based on Gutsy:

[http://howtoforge.com/snort-ossec-prelude-on-ubuntu-gutsy-gibbon](http://howtoforge.com/snort-ossec-prelude-on-ubuntu-gutsy-gibbon)

I read all tut and realize that the minimal requirements, on Ubuntu 8.10, are mysql, the package prelude-manager and its dependence.

So I begin with

```
apt-get install prelude-manager
```

during installation the package keep out more of 4 hours on a Pentium_III-1.3Ghz to generate the cryptography key that it will use to comunicate with the agents (prelude-lml).

Installation was done and I start the server

```
/etc/init.d/prelude-manager start
```

I look in the process to see if it was started

```
ps -fe | grep manager
```

but I can't see it! So I look in syslog and I found this

```
tail /var/log/syslog

[...]

Dec 22 02:51:33 ubuntu8 kernel: [36153.392001] prelude-manager[6498]: segfault at 0 ip b7d50d28 


```

My questions are:

1) Are there someone that get prelude-manager installed on Ubuntu 8.10 without any problem?

2) How many time it keep to do the cryptography key and what is your hardware config?

3) If your syslog report some things about prelude, can you post it here?

Thank you to everyone who spend time to help me to understand where I'm going wrong with the installation of this great product.

max

---

### Post by max_at_app on 2008-12-23
Has anyone installed Prelude-Manager?

please help me...

can you try to install it on a virtual box and tell me if it work?

thx

---

### Post by wHEREiSmYcAPSlOCKkEY on 2009-01-20
Have the same issue, my SSH session fell during the key generation; I ran a 
```
sudo apt-get remove --purge prelude-manager
```
and a
```
sudo find / -name prelude* |sudo xargs rm -rf
```

then reinstalled again, but still prelude-manager doesn't start because of the segfault.

---

### Post by cjacobsen on 2009-01-23
A quick question, Prelude vs SNORT or running both applications at once?

---

