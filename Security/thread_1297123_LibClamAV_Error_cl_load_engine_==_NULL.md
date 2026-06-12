---
title: "LibClamAV Error: cl_load: engine == NULL"
date: 2009-10-21
forum: Security
---

### Post by anupamk on 2009-10-21
Hi,

I have installed ubuntu 9.04 server on one my vm server instance. After 2-3 hours, apache server goes down. When I look at apache error logs I see following statement when the process goes down:

LibClamAV Error: cl_load: engine == NULL.

Version of Clamav is : 0.95.2/9921/Tue Oct 20 23:15:50 2009

I have updated several times thru apt-get update command but the problem still persists.

Any help to fix this issue will be greatly appreciated.

Thnks
Anupam

---

### Post by daliusm on 2009-11-17
> **anupamk said:**
> Hi,

I have installed ubuntu 9.04 server on one my vm server instance. After 2-3 hours, apache server goes down. When I look at apache error logs I see following statement when the process goes down:

LibClamAV Error: cl_load: engine == NULL.

Version of Clamav is : 0.95.2/9921/Tue Oct 20 23:15:50 2009

I have updated several times thru apt-get update command but the problem still persists.

Any help to fix this issue will be greatly appreciated.

Thnks
Anupam

same situation with ubuntu 8.04 and clamav 0.95.3. Apache2 stops after some time.

---

### Post by acidcortex on 2010-03-15
I use php5-clamavlib on production servers for a while and it works nice.
Here's my fix:
When clamav.so extension is loaded, apache2 forks use around 100MB of ram (each). That's because every fork has a whole signature database loaded. When clamav-freshclam updates signature database it cannot reload php module because mod_prefork keeps certain (configured) amount of preforked apaches waiting. Consequently clamav.so extension deadlocks preforked apaches and apache dies.

The fix is:

1. in /etc/php5/apache2/php.ini comment out extension loading line but leave the configuration lines like this:
```
;extension=clamav.so
[clamav]
clamav.dbpath=/var/lib/clamav
clamav.maxreclevel=0
clamav.maxfiles=0
clamav.archivememlim=0
clamav.maxfilesize=0
```(this is default config, I suggest that you set up some limits)

2. enable dynamic module loading in /etc/php5/apache2/php.ini like this
```
enable_dl = On
```

3. when you need to scan something just add this line in your php script
```
dl('clamav.so');
```

This way clamav database/engine update can be performed any time because none of the preforked modules have clamav engine attached. Apache will be faster this way and it will use less memory. And if somehow database update occurs while some slow script is running, it will wait for script to finish and reload it just fine.
Mind that if php5-clamavlib package is upgraded you need to comment-out module loading line again (repeat first step only).

Tested on ubuntu 8.04, clamav 0.94 and 0.95.3, php5-clamavlib 0.13-1.2ub (libclamav5 and libclamav6)

---

