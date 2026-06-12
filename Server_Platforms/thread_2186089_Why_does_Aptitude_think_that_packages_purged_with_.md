---
title: "Why does Aptitude think that packages purged with dpkg need to be reinstalled?"
date: 2013-11-05
forum: Server Platforms
---

### Post by mdlueck on 2013-11-05
I have noticed using Aptitude to apply updates, and dpkg -P to purge off old kernel versions, that after purging old kernel versions, Aptitude wants to reinstall the old kernel packages next time I am in there to apply updates.

As is, I must tell Aptitude to forget pending changes / available updates, re-download the list of packages, mark all upgradable, THEN it correctly marks only the upgrades and does not offer to reinstall old kernel packages which I have purged off with dpkg -P.

Why do Aptitude / dpkg not keep better track of what packages I do / do not want installed? TIA!

---

### Post by stmiller on 2013-11-05
Don't use aptitude? :)  /ducks

---

### Post by mdlueck on 2013-11-05
> **stmiller said:**
> Don't use aptitude?

That is not a helpful solution nor explanation of where the two programs get their wires crossed.

You could have suggested purging with Aptitude as well as applying updates... which I would have responded that it is faster for me to purge off old packages with dpkg than Aptitude.

---

### Post by houstonbofh on 2013-11-06
After purging are you doing an "apt-get update" to refresh everything?

---

### Post by mdlueck on 2013-11-06
> **houstonbofh said:**
> After purging are you doing an "apt-get update" to refresh everything?

No I was not. Merely the dpkg -P and that was all. I can add the "apt-get update" to see if that clears the Aptitude nonsense at the next kernel update. Thank you for the suggestion.

---

### Post by mdlueck on 2013-11-08
> **houstonbofh said:**
> After purging are you doing an "apt-get update" to refresh everything?

Nope, not the fix. Today I updated the kernel on a 12.04 server, IPL, then purge off the old kernel. Entering Aptitude, pressing "U" to mark packages needing upgrading, it selected the prior kernel packages for re-installation that had just been purged off.

Further suggestions than issuing an "apt-get update"?

---

### Post by bild85 on 2013-12-17
I experience this as well. I've purged old kernels using a varient of [this one-liner]("http://www.tolaris.com/2012/07/19/removing-old-kernels-from-ubuntu/"), but when I launch aptitude it tries to reinstall them:```
--\ Packages to be installed (10)                                                                                                                                         
pi   linux-headers-2.6.32-48                                                                                                                 +76.3MB <none>     2.6.32-48.
pi   linux-headers-2.6.32-48-server                                                                                                          +9,347k <none>     2.6.32-48.
pi   linux-headers-2.6.32-49                                                                                                                 +75.9MB <none>     2.6.32-49.
pi   linux-headers-2.6.32-49-server                                                                                                          +9,413k <none>     2.6.32-49.
pi   linux-headers-2.6.32-50                                                                                                                 +75.9MB <none>     2.6.32-50.
pi   linux-headers-2.6.32-50-server                                                                                                          +9,413k <none>     2.6.32-50.
pi   linux-headers-2.6.32-51                                                                                                                 +75.9MB <none>     2.6.32-51.
pi   linux-headers-2.6.32-51-server                                                                                                          +9,363k <none>     2.6.32-51.
pi   linux-headers-2.6.32-52                                                                                                                 +75.9MB <none>     2.6.32-52.
pi   linux-headers-2.6.32-52-server                                                                                                          +9,413k <none>     2.6.32-52.
```

While apt-get dist-upgrade returns "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
Is this a bug against aptitude?

---

### Post by houstonbofh on 2014-01-11
When you "purge the kernel" what exactly are you purging?  There are three packages for each version, and only getting some will leave dependencies...
```
lee@dev01:/boot$ dpkg -l | grep 3.5.0-40
ii  linux-headers-3.5.0-40                       3.5.0-40.62~precise1                             Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-40-generic               3.5.0-40.62~precise1                             Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-40-generic                 3.5.0-40.62~precise1                             Linux kernel image for version 3.5.0 on 64 bit x86 SMP

```

---

### Post by philinux on 2014-01-11
Sounds like aptitude is not purging all 3 bits.

For removing old kernels I use this.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

