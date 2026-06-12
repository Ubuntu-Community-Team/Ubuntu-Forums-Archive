---
title: "Partially failed 9.10 to 10.4 upgrade (mysql not upgraded)"
date: 2010-07-29
forum: Server Platforms
---

### Post by pjs_gsy on 2010-07-29
Hi,

I just did an online upgrade to 10.4.  Upgraded everything first.  Stopped mysql, ran through the upgrade.  The main reason I did this was to get mysql 5.1.  After the upgrade was complete, everything works fine but mysql is still 5.0

I have this in the upgrade logs

2010-07-29 20:33:40,145 DEBUG package 'mysql-client-5.0' has unwanted removals, skipping
2010-07-29 20:33:40,416 DEBUG 'mysql-client-5.0' scheduled for remove but not safe to remove, skipping
2010-07-29 20:33:49,440 DEBUG package 'mysql-server-5.0' has unwanted removals, skipping
2010-07-29 20:33:50,198 DEBUG 'mysql-server-5.0' scheduled for remove but not safe to remove, skipping
2010-07-29 20:33:58,322 DEBUG package 'libmysqlclient15off' has unwanted removals, skipping
2010-07-29 20:33:58,578 DEBUG 'libmysqlclient15off' scheduled for remove but not safe to remove, skipping
2010-07-29 20:34:00,623 DEBUG package 'mysql-server-core-5.0' has unwanted removals, skipping
2010-07-29 20:34:01,100 DEBUG 'mysql-server-core-5.0' scheduled for remove but not safe to remove, skipping      

Any idea how I safely upgrade mysql, preserving all data of course!? 

Thanks.

---

### Post by cdenley on 2010-07-29
How did you upgrade?

I think this command would work, but I'm not 100% sure.
```

sudo apt-get install mysql-server-5.1 mysql-client-5.1

```
You might want to backup your databases first, just in case.

---

### Post by pjs_gsy on 2010-07-30
I did an apt-get upgrade first as advised in the 10.4 release notes to get 9.1 up to date, then the distr-upgrade.  I only said no to not overwrite my.cnf as I have customisations in there I need to keep (it's part of a master/slave) setup.

I'll try upgrading mysql with that command line later when the servers not so busy and see if that works.

Thanks.

---

### Post by pjs_gsy on 2010-07-30
Hmmm, that gives me

>apt-get install mysql-server-5.1 mysql-client-5.1
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
  linux-restricted-modules-2.6.28-11-server: Depends: linux-restricted-modules-common but it is not installable
  mysql-client-5.1: Depends: mysql-client-core-5.1 (>= 5.1.41-3ubuntu12.3) but it is not going to be installed
                    Conflicts: mysql-client-5.0 but 5.1.30really5.0.83-0ubuntu3 is to be installed
  mysql-server-5.1: Depends: mysql-server-core-5.1 (>= 5.1.41-3ubuntu12.3) but it is not going to be installed
                    Conflicts: mysql-server (< 5.1.41-3ubuntu12.3)
                    Conflicts: mysql-server-5.0 but 5.1.30really5.0.75-0ubuntu10.5 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by cdenley on 2010-07-30
I don't know where linux-restricted-modules-2.6.28-11-server came from. You must have that marked for installation or something. That package is for 9.04, though. Are you sure you upgraded from 9.10?

For mysql, assuming you backed up your databases, after you unmark that 9.04 package or whatever, I would try removing mysql-5.0 then installing mysql-5.1.
```

sudo apt-get remove ^mysql
sudo apt-get install mysql-server-5.1 mysql-client-5.1

```
Your actual databases shouldn't be deleted unless you purge, I think.

---

### Post by pjs_gsy on 2010-07-30
Errr, thought so, but maybe not!  Checked the logs to be sure but can;t find anywhere it says which version it started on. I did think I have checked they were all 9.10.  If is was 9.04, have I totally screwed it up!?  Surely it would not upgrade if wrong version?

---

### Post by cdenley on 2010-07-30
> **pjs_gsy said:**
> Errr, thought so, but maybe not!  Checked the logs to be sure but can;t find anywhere it says which version it started on. I did think I have checked they were all 9.10.  If is was 9.04, have I totally screwed it up!?  Surely it would not upgrade if wrong version?

I'm pretty sure going from 9.04 directly to 10.04 isn't supported. I wouldn't expect a "do-release-upgrade" to attempt it, then. However, I wouldn't expect it not to install the new version of mysql either, though.

---

### Post by pjs_gsy on 2010-07-30
think I might start over and just copy /var/lib/mysql across!

Thanks.

---

### Post by cdenley on 2010-07-30
> **pjs_gsy said:**
> think I might start over and just copy /var/lib/mysql across!

Thanks.

I wouldn't do that. I would imagine that the upgrade requires the data to be changed in some way. Maybe copy the data over using a mysqldump backup.

---

### Post by pjs_gsy on 2010-07-30
I think mysql itself upgrades tables as needed on start.  I'll try it on a test machine first.

---

