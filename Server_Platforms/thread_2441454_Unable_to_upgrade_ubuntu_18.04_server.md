---
title: "Unable to upgrade ubuntu 18.04 server"
date: 2020-04-23
forum: Server Platforms
---

### Post by deepakdeshp on 2020-04-23
Hello.
I did ```
apt update&&apt upgrade; apt dist-upgrade;
```. Then ```
sudo do-release-upgradeChecking for a new Ubuntu release
There is no development version of an LTS available.
To upgrade to the latest non-LTS develoment release 
set Prompt=normal in /etc/update-manager/release-upgrades.
```

Thanks for any replies.

---

### Post by Bashing-om on 2020-04-23
deepakdeshp; Hello

The release-upgrade command is:
```

sudo do-release-upgrade -d

```
where the "d" switch is for (D)evelopment. Focal remains in this development channel until the 1st point release (23Jul).

[INDENT]this should help[/INDENT]

---

### Post by darkod on 2020-04-23
Please note that using -d is not really recommended. The version 20.04 will become available usually after the first point release is out, 20.04.1 and that is sometime in the summer.

Unless you have a reason to rush with the upgrade, I would wait instead of using -d.

---

