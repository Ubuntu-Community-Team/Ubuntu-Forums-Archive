---
title: "Help with Upgrade"
date: 2011-04-26
forum: Server Platforms
---

### Post by lucacerone on 2011-04-26
Dear all,
when connecting to the server I administrate,
I have a welcome message like:
> Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

14 packages can be updated.
10 updates are security updates.
Whenever I try to update the list of packages and upgrade them
> sudo apt-get update && sudo apt-get upgrade .
I get a message saying that no package to upgrade is available:
> 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded..

Why is that? How can I be sure that my server is updated, or how can I restore apt-get to work?

Thanks a lot in advance,
Cheers, -Luca

---

### Post by matt_symes on 2011-04-26
Hi

Are any package being held back ?

Kind regards

---

### Post by lucacerone on 2011-04-26
As far as I know no...
How can I check it?
Thanks for your help!

---

### Post by rubylaser on 2011-04-26
You'd have a section like this after your apt-get upgrade
```
[COLOR="Red"]The following packages have been kept back:
  linux-headers-server linux-image-server linux-server[/COLOR]
The following packages will be upgraded:
  initscripts libdbus-1-3 libwbclient0 linux-firmware linux-libc-dev logrotate
  ntpdate openssh-client openssh-server samba samba-common samba-common-bin
  smbfs sysv-rc sysvinit-utils tzdata w3m
17 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 29.6MB of archives.
After this operation, 901kB of additional disk space will be used.
```

To resolve this, you need to do a dist-upgrade
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

