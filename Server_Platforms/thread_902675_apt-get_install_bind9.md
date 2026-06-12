---
title: "apt-get install bind9"
date: 2008-08-27
forum: Server Platforms
---

### Post by timmillwood on 2008-08-27
I am trying to setup bind9, but I'm a newbie.

```

root@server:/tmp# apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ssl-cert openssl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdns35 libisc32 libisccc30 libisccfg30 libxfixes3
Suggested packages:
  bind9-doc dnsutils resolvconf
The following NEW packages will be installed:
  bind9 libdns35
The following packages will be upgraded:
  libisc32 libisccc30 libisccfg30 libxfixes3
4 upgraded, 2 newly installed, 0 to remove and 53 not upgraded.
1 not fully installed or removed.
Need to get 0B/958kB of archives.
After this operation, 2138kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `libxfixes3' missing, assuming package has no files currently installed.
16430 files and directories currently installed.)
Preparing to replace libxfixes3 1:4.0.3-2 (using .../libxfixes3_1%3a4.0.3-2_i386.deb) ...
Unpacking replacement libxfixes3 ...
Preparing to replace libisc32 1:9.4.2-10 (using .../libisc32_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisc32 ...
Selecting previously deselected package libdns35.
Unpacking libdns35 (from .../libdns35_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Preparing to replace libisccc30 1:9.4.2-10 (using .../libisccc30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisccc30 ...
Preparing to replace libisccfg30 1:9.4.2-10 (using .../libisccfg30_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Unpacking replacement libisccfg30 ...
Selecting previously deselected package bind9.
Unpacking bind9 (from .../bind9_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Setting up libxfixes3 (1:4.0.3-2) ...

Setting up libisc32 (1:9.4.2-10ubuntu0.1) ...

Setting up libdns35 (1:9.4.2-10ubuntu0.1) ...

Setting up libisccc30 (1:9.4.2-10ubuntu0.1) ...

Setting up libisccfg30 (1:9.4.2-10ubuntu0.1) ...

Setting up bind9 (1:9.4.2-10ubuntu0.1) ...
 * Starting domain name service... bind
   ...fail!

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
root@server:/tmp# 


```

---

### Post by timmillwood on 2008-08-27
Tried updating sources.list from list on [http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts) but got a new error 

```

root@server:/tmp# apt-get install bind9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bind9 is already the newest version.
The following packages were automatically installed and are no longer required:
  ssl-cert openssl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
1 not fully installed or removed.
Need to get 0B/61.2kB of archives.
After this operation, 0B of additional disk space will be used.
Use of uninitialized value in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Out of memory!
(Reading database ... 16468 files and directories currently installed.)
Preparing to replace libpam-runtime 0.99.7.1-5ubuntu6 (using .../libpam-runtime_0.99.7.1-5ubuntu6_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libpam-runtime_0.99.7.1-5ubuntu6_all.deb (--unpack):
 fork failed: Cannot allocate memory
dpkg: error while cleaning up:
 fork failed: Cannot allocate memory
dpkg: error while cleaning up:
 fork failed: Cannot allocate memory
Errors were encountered while processing:
 /var/cache/apt/archives/libpam-runtime_0.99.7.1-5ubuntu6_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:/tmp# 


```

---

### Post by timmillwood on 2008-08-27
not really sure what i did, but now working

---

