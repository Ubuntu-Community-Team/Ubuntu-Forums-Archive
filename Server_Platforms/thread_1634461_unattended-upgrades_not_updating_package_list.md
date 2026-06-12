---
title: "unattended-upgrades not updating package list"
date: 2010-11-30
forum: Server Platforms
---

### Post by hubbub on 2010-11-30
I've followed the [ubuntu guide]("https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html") for implementing automatic updates, all of the settgin lsited match mine, but it appears to not update package lists.

If I run ```
sudo unattended-upgrade --debug --dry-run
```

no packages are identified for updating

then I manually run ```
sudo apt-get update
``` to update packages lists

and run CODE]sudo unattended-upgrade --debug --dry-run[/CODE] for a second time

a pkg (dpkg) is identified for upgrading.

so it appears to not run update, even though ```
APT::Periodic::Update-Package-Lists "1";
``` is configured in /etc/apt/apt.conf.d/10periodic

settings for ubuntu server 10.04:

/etc/apt/apt.conf.d/50unattended-upgrades
```
Unattended-Upgrade::Allowed-Origins {
     "Ubuntu lucid-security";
     "Ubuntu lucid-updates";
};
```

/etc/apt/apt.conf.d/10periodic
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";
```

Any suggestions on how to ensure the package lists are updated?

Thank you.

---

