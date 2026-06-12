---
title: "auto connecting to Amazon Web Services after boot"
date: 2012-04-18
forum: Security
---

### Post by Soul-Sing on 2012-04-18
=Amazon Web Services, Elastic Compute Cloud, EC2, EU=
shows up via ```
netstat -taupen
```

tcp        0      0 10.0.2.15:42967         46.137.32.111:80

when config. ufw with outbound rules the same ip address shows up as blocked in the ufw logs.(port 80) in endless strings of blocked traffic.
Is this ip adrress in some way related with/to ubuntu-(one) ?
Should I allow acces or not?

---

### Post by cariboo on 2012-04-18
UbuntuOne is hosted on Amazon's servers, if you use it allow it, if you don't use UbuntuOne, you can probably uninstall the client. I'm running Precise, so I can't tell you exactly what packages to uninstall.

---

### Post by Soul-Sing on 2012-04-18
> **cariboo907 said:**
> UbuntuOne is hosted on Amazon's servers, if you use it allow it, if you don't use UbuntuOne, you can probably uninstall the client. I'm running Precise, so I can't tell you exactly what packages to uninstall.

Thank for the info carboo907. I don't use ubuntu-one and removed the ubuntu-one client via synaptic. I 'll take a look how to kill the ubuntu-one rsync daemon that shows up in process managment.

---

### Post by Soul-Sing on 2012-04-18
via: [https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/)

I completely removed ubuntu-one from my system. However the ip address still finds its way in my ufw logs. Bit strange this imo.

---

### Post by cariboo on 2012-04-21
Does:

```
sudo lsof -n -P -i
```

tell you which service is connecting to that ip address?

---

### Post by Soul-Sing on 2012-04-21
After config. outbound rules, the amazon ip adres is only present as blocked in the ufw logs. Some days ago I disabled my ubuntuone account. (I on't use it) And since yesterday my ufw logs are empty. the "hamering"ip adres via/from amazon web is gone.
(It is by the way not possible to delete a ubuntuone account)

---

### Post by Soul-Sing on 2012-04-21
> **cariboo907 said:**
> Does:

```
sudo lsof -n -P -i
```

tell you which service is connecting to that ip address?

7u  IPv4  11814      0t0  TCP xxxxxxxxx:50403->91.189.89.144:80 (CLOSE_WAIT)
unity-sco 2081   leoquant    8u  IPv4  13093      0t0  TCP xxxxxxxxx:60683->91.189.89.134:80 (CLOSE_WAIT)
unity-sco 2081   leoquant   14u  IPv4  13094      0t0  TCP xxxxxxxxx:60684->91.189.89.134:80 (CLOSE_WAIT)

---

### Post by cariboo on 2012-04-22
From you lsof output, it could very well be:

[LIST]
[*]unity-scope-musicstore
[*]unity-scope-video-remote
[/LIST]

Both are installed by default, and easily removed if not needed.

---

### Post by Soul-Sing on 2012-04-22
thx again! only [COLOR="Red"]ubuntu geo-ip[/COLOR] is left. But thats not an easy remove. (If not impossible, because the data server will break afaik)

---

### Post by cariboo on 2012-04-23
Geo-ip connects directly to Ubuntu on my system, so if you trust them, there's nothing to worry about. :)

---

### Post by Soul-Sing on 2012-04-23
> **cariboo907 said:**
> Geo-ip connects directly to Ubuntu on my system, so if you trust them, there's nothing to worry about. :)
Indeed :) thx a bunch. I should be more around in #ubuntu+1. 
comment from ken vandine bout geo ip:


> There is currently no way to disable the geoip check. It is currently used to determine if your timezone has changed. In the future we should really add an option to disable it or at least reduce the dependency on the geoclue-ubuntu-geoip package to a recommends so users can just un-install that. I just tested that and it breaks indicator-datetime, I will make sure that gets addressed for 12.10.

(source: askubuntu)

---

