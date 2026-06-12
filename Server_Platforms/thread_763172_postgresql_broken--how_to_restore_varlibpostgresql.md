---
title: "postgresql broken--how to restore /var/lib/postgresql/8.2/main ?"
date: 2008-04-22
forum: Server Platforms
---

### Post by _fool on 2008-04-22
hi folks,

i was playing with a postgresql installation on gutsy and made some users and granted them permissions via a readme for some software i was trying to setup.  i wanted a clean slate, so i removed apt-get remove'd postgresql postgresql-client, and reinstalled them.  unfortunately, the permissions i'd set up before persisted, so i re-removed the packages, and saw that /var/lib/postgresql/8.2/main directory remained and was full of files.  so i removed that directory manually, thinking that it contained the saved state.

unfortunately upon reinstallation of the packages, that directory does not reappear and the db server does not work--the init script claims to start it successfully, but the process is not running and the log is not updated.

i went to another ubuntu machine to try to figure out what package "owned" that directory to reinstall it, but dpkg -S claimed nobody owned it.  sigh.

how can i get it back?

this is 64bit/x86 gutsy, and i have the following postgresql packages installed:

ii  postgresql                              8.2.7-0ubuntu0.7.10                  object-relational SQL database (latest version)
ii  postgresql-8.2                          8.2.7-0ubuntu0.7.10                  object-relational SQL database, version 8.2 server
ii  postgresql-client                       8.2.7-0ubuntu0.7.10                  front-end programs for PostgreSQL (latest version)
ii  postgresql-client-8.2                   8.2.7-0ubuntu0.7.10                  front-end programs for PostgreSQL 8.2

thanks in advance for your help!

---

### Post by geertn on 2008-04-23
Indeed something seems strange with the 8.2 package. The 8.3 package will purge /var/lib/postgresql, /var/log/postgresql and /etc/postgresql. 8.2 package does not.

This will give you a clean slate:
```
apt-get --purge remove postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common

mv /var/lib/postgresql /var/lib/postgresql-backup
mv /etc/postgresql /etc/postgresql-backup
mv /var/log/postgresql /var/log/postgresql-backup

```

This will install postgres again (on gutsy release 8.3, which you'd probably want)
```
apt-get install postgresql
```

else pick 8.2
```
apt-get install postgresql-8.2
```

---

### Post by _fool on 2008-04-23
thanks for your response, geertn.  unfortunately, the purge and reinstall (i can't find version 8.3 for gutsy on packages.ubuntu.com?) did not do the trick--/var/lib/postgresql/8.2/main did not magically reappear, and the server (though it claims below to have been started) does not start.

i re-purged and installed postgresql-8.1 to see if it worked better, and it did--it created /var/lib/postgresql/8.1/main and the server started up just fine.

but even after co-installing 8.2, the server still wouldn't start.  i removed 8.1 with --purge and it did indeed get rid of the /var/lib/postgresql/8.1/main directory.

strangely, i installed postgresql on gutsy on a virtual machine i just setup and installing the same postgresql-8.2 package does create a /var/lib/postgresql/8.2/main cluster.  sigh.  that just never actually happens on my main machine during the install.

ideas?


fool@kailarose:~$ sudo apt-get install postgresql
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common
Suggested packages:
  postgresql-doc-8.2
The following NEW packages will be installed:
  postgresql postgresql-8.2 postgresql-client-8.2 postgresql-client-common postgresql-common
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/4565kB of archives.
After unpacking 17.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package postgresql-client-common.
(Reading database ... 49044 files and directories currently installed.)
Unpacking postgresql-client-common (from .../postgresql-client-common_78_all.deb) ...
Selecting previously deselected package postgresql-client-8.2.
Unpacking postgresql-client-8.2 (from .../postgresql-client-8.2_8.2.7-0ubuntu0.7.10_amd64.deb) ...
Selecting previously deselected package postgresql-common.
Unpacking postgresql-common (from .../postgresql-common_78_all.deb) ...
Selecting previously deselected package postgresql-8.2.
Unpacking postgresql-8.2 (from .../postgresql-8.2_8.2.7-0ubuntu0.7.10_amd64.deb) ...
Selecting previously deselected package postgresql.
Unpacking postgresql (from .../postgresql_8.2.7-0ubuntu0.7.10_all.deb) ...
Setting up postgresql-client-common (78) ...
Setting up postgresql-client-8.2 (8.2.7-0ubuntu0.7.10) ...

Setting up postgresql-common (78) ...
/bin/df: `/var/lib/postgresql/8.2/main': No such file or directory

Setting up postgresql-8.2 (8.2.7-0ubuntu0.7.10) ...
 * Starting PostgreSQL 8.2 database server
   ...done.

Setting up postgresql (8.2.7-0ubuntu0.7.10) ...

---

### Post by geertn on 2008-04-24
Did you perform the following after purging the packages?

```

mv /var/lib/postgresql /var/lib/postgresql-backup
mv /etc/postgresql /etc/postgresql-backup
mv /var/log/postgresql /var/log/postgresql-backup

```

I noticed that the package checks for existence of these directories when installing. If one of them exist, it will assume it is a reinstall and not create /var/lib/postgresql.

---

### Post by _fool on 2008-04-24
that didn't seem to work, but removing the directories entirely did the trick.  thanks for your help!

---

### Post by garolou on 2009-03-30
I also got stumped trying to reinstall postgresql 8.3 even after a purge and deleting all references to postgresql... "/var/lib/postgresql/8.3/main" directory would not be created. The solution was to also remove the postgres user and reinstall.
```
sudo userdel postgres
sudo apt-get install postgresql-8.3
```

---

### Post by jsavimbi on 2009-06-11
I'm getting these errors when uninstalling/reinstalling 8.3 following the above mentioned instructions:

```
Setting up postgresql-8.3 (8.3.7-1) ...

Errors were encountered while processing:
 moodle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ides?

---

