---
title: "32 or 64 bit server?"
date: 2011-08-07
forum: Server Platforms
---

### Post by NetDoc on 2011-08-07
Is there a way to differentiate between a 32 bit and 64 bit distro from the command line? 

I also need to know this for a CentOS 5 box.

---

### Post by haqking on 2011-08-07
> **NetDoc said:**
> Is there a way to differentiate between a 32 bit and 64 bit distro from the command line? 

I also need to know this for a CentOS 5 box.

you mean how to tell if your running n32 or 64 bit ?

uname -a

or

uname -m to be more specific

---

### Post by NetDoc on 2011-08-07
> **haqking said:**
> you mean how to tell if your running n32 or 64 bit ?

uname -a

or

uname -m to be more specific This is telling me about the processor or the OS? 

Here is the result of uname -a

Alpha
```
Linux alpha.scubaboard.com 2.6.18-128.1.10.el5 #1 SMP Thu May 7 10:35:59 EDT 2009 x86_64 x86_64 x86_64 GNU/Linux

```
Beta
```
Linux beta 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux

```
Gamma
```
Linux gamma 2.6.24-23-server #1 SMP Wed Apr 1 22:14:30 UTC 2009 x86_64 GNU/Linux
```
Delta
```
Linux delta 2.6.24-24-server #1 SMP Wed Apr 15 15:41:09 UTC 2009 x86_64 GNU/Linux

```

So I guess that they are all 64 bit servers?

From Gamma: cat /proc/version
```
Linux version 2.6.24-24-server (buildd@yellow) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu4)) #1 SMP Wed Apr 15 15:41:09 UTC 2009

```

---

