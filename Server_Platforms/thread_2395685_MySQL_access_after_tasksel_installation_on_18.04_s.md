---
title: "MySQL access after tasksel installation on 18.04 server"
date: 2018-07-05
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2018-07-05
Hi

Basic installation followed by :-

```
sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get install tasksel -y
sudo tasksel
```

LAMP was additionally selected in tasksel, but, unlike previous versions did not request a password for MySQL during installation.
Xubuntu desktop was also included, as well as the normal defaults.

After rebooting,
```
/etc/init.d/mysqld status
```produces 'No such file or directory'
```
mysql -u root -p
```fails as no password has been assigned even if MySQL were to be running.

What's missing please?

TIA

---

### Post by Doug S on 2018-07-05
I don't know about your status, but mysql no longer uses it's own root password. See also [here]("https://bugs.launchpad.net/ubuntu/+source/mysql-5.7/+bug/1752215").

EDIT: Where you used to do this:```
mysql -u root -p
```you would now do this:```
sudo mysql
```

---

### Post by ChrisRChamberlain on 2018-07-06
Doug S

Many thanks for the link - was unaware of the change.

---

