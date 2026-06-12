---
title: "Kmymoney 8.5"
date: 2006-08-31
forum: Ubuntu Backports
---

### Post by wangbo on 2006-08-31
Being relatively new to Ubuntu I'm hoping that this is the right place to request updated packages. Kmymoney 8.5 was released today and hoping to see the updated package in dapper drake  If this isn't the appropos p[laxe then where to request for packages. Thanks in advance.

---

### Post by mlind on 2006-09-06
[http://ubuntuforums.org/showthread.php?t=153402](http://ubuntuforums.org/showthread.php?t=153402)

Backport will probably take some time, you can try this package in the meantime:
[http://www.freefilehoster.com/uploads/1157545625kmymoney2_0.8.5-dapper.tar.gz](http://www.freefilehoster.com/uploads/1157545625kmymoney2_0.8.5-dapper.tar.gz)

---

### Post by wangbo on 2006-09-07
Awesome and thanks will give her a try tonight.

---

### Post by wangbo on 2006-09-08
Downloaded and installed it and works like a champ, Installed with out a hitch. Haven't found any problems yet. Good job and Thanks again.

---

### Post by dwangoac on 2007-03-06
Hmm...  I installed the 0.8.5 version linked above and it installed without complaining about any dependencies, but it's throwing a SIGSEGV error on launch.  I have no idea if this is useful or not, but here's the Backtrace information:

```
[KCrash handler]
#6  0xb5d1ec64 in free () from /lib/tls/i686/cmov/libc.so.6
#7  0xb5d2083f in malloc () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7d19496 in GWEN_Buffer_new () from /usr/lib/libgwenhywfar.so.17
#9  0xb7d96b1e in GWEN_Path_HandleWithIdx () from /usr/lib/libgwenhywfar.so.17
#10 0xb7d83578 in GWEN_DB_GetNode () from /usr/lib/libgwenhywfar.so.17
#11 0xb7d867b4 in GWEN_DB_GetGroup () from /usr/lib/libgwenhywfar.so.17
#12 0xb7d23f02 in GWEN_PathManager_DefinePath ()
   from /usr/lib/libgwenhywfar.so.17
#13 0xb7dfe2ad in AB_Banking_Init () from /usr/lib/libaqbanking.so.0
#14 0xb7e627ce in Banking::init () from /usr/lib/libqbanking.so.1
#15 0xb7e60190 in QBanking::init () from /usr/lib/libqbanking.so.1
#16 0xb5695e86 in KBanking::init () from /usr/lib/libkbanking.so.1
#17 0xb56c5591 in KBankingPlugin::KBankingPlugin ()
   from /usr/lib/kde3/kmm_kbanking.so
#18 0xb56c6f78 in KGenericFactory<KBankingPlugin, QObject>::createObject ()
   from /usr/lib/kde3/kmm_kbanking.so
#19 0xb6d22c21 in KLibFactory::create () from /usr/lib/libkdecore.so.4
#20 0x080f9f1a in KMyMoney2App::loadPlugins ()
#21 0x080fb7b1 in KMyMoney2App::KMyMoney2App ()
#22 0x080fe5b5 in main ()
```

I'll have to keep digging on this one.  I had previously compiled version 0.8.5 from source (in Dapper, prior to upgrading to Edgy which caused this failure int he first place).  I'll post here if I figure out a solution.  Thanks,

A.C.
******

---

### Post by msak007 on 2007-03-11
I usually have to end up compiling KMyMoney and its main dependencies (aqbanking and gwenhywfar) from source because the version in the repos isn't compiled with the "aqofxconnect" backend, which I need in order to use OFX DirectConnect and download statements from my bank online (I'm in the US). You've already compiled once, you might as well try again and upgrade to version 0.8.6 which just came out a couple days ago. I'm using that on my main desktop now and trying the 0.9 CVS development version on my laptop.

---

### Post by mlind on 2007-03-12
Binary was compiled for Dapper. Do you need one for Edgy ?

---

