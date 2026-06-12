---
title: "soft lookup_cpu#3 stuck for 61s"
date: 2009-04-20
forum: Server Platforms
---

### Post by silbro on 2009-04-20
Hello everybody,

I've had a weird problem. I got the following error on a server:

```
[]BUG: soft lockup_CPU#3 stuck for 61s
```

The server was running for days actually weeks without any problems. Then this error popped up all of a sudden. I've googled for this, it is said to be a bug. Any ideas?

thx in advance!
Sil

Edit:

Here are the latest log entries from kern and syslog

**Syslog**
```
Apr 17 22:00:01 EFL-S00 ntpdate[24085]: adjust time server 91.189.94.4 offset 0.046786 sec
```

**kern**
```
Apr 17 21:50:01 EFL-S00 kernel: [1495414.703600] console-kit-dae[23933]: segfault at 58 ip 00007f77c4abde09 sp 0000000040f72090 error 4 in libglib-2.0.so.0.1800.2[7f77c4a91000+c3000]

```

---

### Post by silbro on 2009-04-28
*bump* 

;)

---

