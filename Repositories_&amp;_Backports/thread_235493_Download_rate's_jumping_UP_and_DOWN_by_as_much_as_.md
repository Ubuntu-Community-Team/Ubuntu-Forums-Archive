---
title: "Download rate's jumping UP and DOWN by as much as 100KB"
date: 2006-08-13
forum: Repositories &amp; Backports
---

### Post by ashrack on 2006-08-13
Having some weird problems with the repos lately. When downloading my DL rate is constantly jumping up and now. Here's an example:

```
Get: 1 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-26 2.6.15-26.46 [6903kB]
16% [1 linux-headers-2.6.15-26 1266880/6903kB 18%]               2604B/s 11m35s

```
and after half a minute of that slow speed it jumps to this:
```
Get: 1 http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-26 2.6.15-26.46 [6903kB]
19% [1 linux-headers-2.6.15-26 1266880/6903kB 18%]               90kB/s 1m15s
```
and then again jumps to the slow speeds. I've observed the same behavior on my computer at home and also on a friends computer whose also running UBUNTU-DAPPER.
This sort of strange behaviour only happens with the official REPOS. 
BUt with the unofficial repos like QUINNs the download rate is constant!

---

### Post by meng on 2006-08-13
I'd experienced exactly this and assumed it was normal.

---

### Post by ashrack on 2006-08-13
this definetly can't be normal.
Because at times I must wait for 10minutes to download a 10MB packet and it doesnt matter which hour

---

### Post by ashrack on 2006-08-18
any answers to this annomily

---

### Post by ashrack on 2006-08-28
come on no one? Currently am at my friends house and I've been DL 150MB repo update for more than two hours. And the speed is around 2KB/s! And I tried different REPOSITORIES even our local one but they are all the same slow!

He has an ADSL 1024Kb/s! And when we tried DL something from then net the speed was 100KB/s! 

What is going with the repos, since now I've had 4reports of this problmem

---

### Post by ashrack on 2007-01-14
I found a solution.Found this unnoficial mirror:
[http://ubuntu.uni-klu.ac.at/ubuntu/](http://ubuntu.uni-klu.ac.at/ubuntu/) 
And from this one everything works great.

ps. How come the official UBUNTU mirrors are so fubar?

---

### Post by hikaricore on 2007-01-15
> **ashrack said:**
> 
ps. How come the official UBUNTU mirrors are so fubar?

My guess would be the thousands of people like myself who compulsively spam "sudo apt-get update" 50 times a day, are kicking the server's arse.  lol

---

