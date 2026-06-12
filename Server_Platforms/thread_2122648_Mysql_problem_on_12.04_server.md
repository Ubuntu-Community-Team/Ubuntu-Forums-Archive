---
title: "Mysql problem on 12.04 server"
date: 2013-03-05
forum: Server Platforms
---

### Post by mobo on 2013-03-05
Trying to do update/upgrade and noticed I had an issue. I suppose it occurred after removing plex from the server. Anyway, when I run the upgrade I get the following that I cannot figure out..Any Help is greatly appreciated.

The following packages have unmet dependencies:
 libmysqlclient18 : Depends: mysql-common (>= 5.5.29-0ubuntu0.12.04.2) but it is not going to be installed
 mysql-client-5.5 : Depends: mysql-common (>= 5.5.29-0ubuntu0.12.04.2) but it is not going to be installed
 mysql-server-5.5 : Depends: mysql-server-core-5.5 (= 5.5.24-0ubuntu0.12.04.1) but 5.5.29-0ubuntu0.12.04.2 is to be installed
                    PreDepends: mysql-common (>= 5.5.24-0ubuntu0.12.04.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by wlraider70 on 2013-03-05
do you have your DBs backed up. You could try removing mysql-common then installing again.

---

### Post by mobo on 2013-03-05
Funny thing is I get the same error when trying to uninstall it.

---

### Post by tgalati4 on 2013-03-05
Try:

```
sudo apt-get -f install
```

And post what it says.

How was plex installed originally?  Via a PPA, deb package or self-installing zip?

How was plex removed?

---

### Post by mobo on 2013-03-05
Looks like i'm heading in the right direction: I used a few other commands in order and got the errors to disappear:
aptitude &#8211;purge remove mysql-server
apitude &#8211;purge remove mysql-client
aptitude &#8211;purge remove mysql-common

apt-get autoremove
apt-get autoclean


aptitude install mysql-server mysql-client mysql-common


The restarted it and boom.

---

