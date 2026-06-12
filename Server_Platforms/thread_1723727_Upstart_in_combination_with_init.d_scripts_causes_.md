---
title: "Upstart in combination with init.d scripts causes a problem when order is important"
date: 2011-04-07
forum: Server Platforms
---

### Post by sigve on 2011-04-07
Hi!

I've got an Ubuntu Server 10.10 with Bacula. Bacula is not using Upstart at boot time, it is started using legacy init.d scripts. MySQL on the other hand uses Upstart. This causes MySQL to start after Bacula, thus preventing Bacula director from connecting to the MySQL database - causing an error.

I've tried to change the order of the init.d scripts in /etc/rc2.d, giving mysql the prefix S20 and bacula prefixes ranging from S90-S93, but to no avail. The bacula scripts are still loading before MySQL.

Can someone please fill me in on how to configure the order of boot scripts when using both Upstart and legacy init.d scripts?

---

### Post by sigve on 2011-04-07
When looking at /var/log/boot.log it seems the boot order is actually correct, but the problem seems to be mysql not starting for some reason. The error in the log is as follows:

> Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S99mysql start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S99mysql
start: Unknown job: S99mysql


---

