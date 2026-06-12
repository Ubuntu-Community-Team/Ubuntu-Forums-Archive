---
title: "Can not upgrade  An upgrade from 'Zesty' to 'zesty' is not supported with this tool."
date: 2016-12-05
forum: Ubuntu Development Version
---

### Post by hoboy on 2016-12-05
After I have upgrade from ubuntu 16.10 to 17.04, each time I use software updater I am asked to do partial apgrade
when I try partial upgrade I get the following error:
 upgrade  An upgrade from 'Zesty' to 'zesty' is not supported with this tool.
--------------------------------------------------------------------------------------------------------------------
 lsb_release -a
LSB Version:	core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu Zesty Zapus (development branch)
Release:	17.04
Codename:	Zesty
--------------------------------------------------

---

### Post by howefield on 2016-12-05
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by terry_gardener on 2016-12-05
have you tried from CLI. this is how i do my updates in development releases 

```
sudo apt-get update
```
then 
```
sudo apt-get dist-upgrade
```

---

### Post by hoboy on 2016-12-06
Yes i have tried sudo apt-get update and sudo apt-get dist-upgrade
that hasn't helped
so I am really perplexed
tks

---

### Post by dino99 on 2016-12-06
I suppose your /etc/apt/sources.list does not only use 'zesty'
Remember to respect the case sensitive rules.

---

### Post by howefield on 2016-12-06
Have a read at this [sticky thread]("https://ubuntuforums.org/showthread.php?t=2340641").

---

