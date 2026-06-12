---
title: "Layer 7 installation snag"
date: 2009-08-03
forum: Server Platforms
---

### Post by Raddy13 on 2009-08-03
Hey guys,

I have an eBox installation acting as the router for our home network, and I wanted to install some advanced traffic shaping so that people seeding torrents and other P2P stuff don't eat up our bandwidth, and so I'm trying to install the L7 filter on the router router, following the instructions I found on the eBox website, but when I follow the instructions, I get this error:

```
raddy@Floodgate:~$ sudo apt-get install ebox-l7-protocols
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ebox-l7-protocols: Depends: ebox (>= 1.1~svn) but 1.0.1-0ubuntu1~ppa1~hardy1 is to be installed
E: Broken packages

```

I also tried doing:
```
raddy@Floodgate:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jabber-muc
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up slapd (2.4.15-1ubuntu3ebox5hardy) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.4.9-0ubuntu0.8.04.2... done.
failed.

Migrating slapd.conf file (/tmp/upgrade_slapd.conf.Pfzyrl2944) to slapd.d failed with the following error while running slaptest:
    /tmp/upgrade_slapd.conf.Pfzyrl2944: line 114: rootdn is always granted unlimited privileges.
    bdb(dc=ebox): Program version 4.6 doesn't match environment version 0.231
    hdb_db_open: database "dc=ebox" cannot be opened, err -30972. Restore from backup!
    backend_startup_one: bi_db_open failed! (-30972)
    slap_startup failed (test would succeed using the -u switch)
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


With no luck.  Am I missing a something from my /etc/apt/sources.list? Any help is greatly appreciated!

Linux Kernel 2.6.24-24 Server
eBox 1.0
Ubuntu Hardy

---

### Post by Raddy13 on 2009-08-04
bump

---

