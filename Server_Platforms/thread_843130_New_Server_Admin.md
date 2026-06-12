---
title: "New Server Admin"
date: 2008-06-28
forum: Server Platforms
---

### Post by wiseph on 2008-06-28
I've just inherited administration of several ubuntu servers.
I haven't used Linux for about 10 years and would like to know how to determine the version, kernel, update history... of the software on the machines.  Any suggestions would be appreciated!
Thanks!  :eek:

---

### Post by Chayak on 2008-06-28
Wow, talk about being tossed into deep water to see if you can swim.

The first thing I'd do would be an 'apt-get update' and an 'apt-get upgrade' on each of the servers in turn just to make sure they're all up to date and if necessary schedule a time for a reboot for any new kernels.

That should take care of all the software and services installed unless they're third party not installed with apt-get.  Those will be on a case by case basis.

I'd do a security audit after that and make sure they're are no extra users with uid 0 running around.

---

### Post by forger on 2008-06-28
For version, kernel (and some other information):
```
uname -a
lsb_release -a
users
id
```

The updates log: **/var/log/dpkg.log**
```
cat /var/log/dpkg.log
```
(All other logs are in /var/log/ directory too)

You should check out the sources list of the software repositories: **/etc/apt/sources.list**
```
cat /etc/apt/sources.list
```
Make sure they're the official repositories

Afterwards update the servers - don't upgrade if you're not sure about the package you're installing:
```
apt-get update
apt-get upgrade
```

The "cache" directory of the apt software: **/var/cache/apt/archives/**

---

### Post by theonegod on 2008-06-30
> **Chayak said:**
> Wow, talk about being tossed into deep water to see if you can swim.

The first thing I'd do would be an 'apt-get update' and an 'apt-get upgrade' on each of the servers in turn just to make sure they're all up to date and if necessary schedule a time for a reboot for any new kernels.

That should take care of all the software and services installed unless they're third party not installed with apt-get.  Those will be on a case by case basis.

I'd do a security audit after that and make sure they're are no extra users with uid 0 running around.

Be carefull doing this wthout knowing what will be upgraded. YOU may find yourself having to recompile some things after doing this. I did this once and part of what was upgraded was the version of php. I had the web developers complaining to me quite quickly.

---

