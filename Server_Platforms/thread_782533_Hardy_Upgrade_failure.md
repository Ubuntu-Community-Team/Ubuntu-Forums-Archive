---
title: "Hardy Upgrade failure"
date: 2008-05-05
forum: Server Platforms
---

### Post by apadula on 2008-05-05
Hi All,

Wondering if anyone here can help me out a little, I just updated one of my servers to Hardy, and it has failed during the package configuration steps, specifically when configuring the LDAP server.  This server's only job is to run LDAP, so that's a pretty big deal.

The upgrade ended like this:

```
Errors were encountered while processing:
 slapd

Could not install the upgrades 

The upgrade aborts now. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

Please report this bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bugreport. 
E:Sub-process /usr/bin/dpkg returned an error code (1) 

Setting up slapd (2.4.7-6ubuntu4.1) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.3.35-1ubuntu0.2... done.
  Upgrading BDB 'checkpoint' options... .
  Moving old database directories to /var/backups:
  Loading from /var/backups/slapd-2.3.35-1ubuntu0.2: 
  - directory dc=nutsngum,dc=com... failed.

Loading the database from the LDIF dump failed with the following
error while running slapadd:
    /etc/ldap/slapd.conf: line 103: rootdn is always granted unlimited privileges.
    slapadd: line 1: database (dc=nutsngum,dc=com) not configured to hold "dc=nodomain"
    slapadd: line 1: database (dc=nutsngum,dc=com) not configured to hold "dc=nodomain"
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd

Could not install the upgrades 

The upgrade aborts now. Your system could be in an unusable state. A 
recovery will run now (dpkg --configure -a). 

Please report this bug against the 'update-manager' package and 
include the files in /var/log/dist-upgrade/ in the bugreport. 
installArchives() failed 

Setting up slapd (2.4.7-6ubuntu4.1) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.3.35-1ubuntu0.2... done.
  Upgrading BDB 'checkpoint' options... .
  Moving old database directories to /var/backups:
  Loading from /var/backups/slapd-2.3.35-1ubuntu0.2: 
  - directory dc=nutsngum,dc=com... 
```


I had a look around and during the configuration it backed up the LDAP database, then tried to reload it from the backup.  What had happened was that the backup contained some "stuff" from the original installation of the LDAP server that shouldn't have been there.  Cleaning up the export and reloading it has successfully got the LDAP server running again, and all is well in that world at the moment.

However, I'm now stuck in the middle of an upgrade.  I have tried running the upgrade again (both with "do-release-upgrade" and "apt-get dist-upgrade") and neither of them do anything.  The first actually says this:

```
Checking for a new ubuntu release
current dist not found in meta-release file
No new release found
```

I'm at a loss to figure out what I need to do to complete the upgrade.  I'm confident that the problem that occurred was due to bad data in the LDAP database export, so I'm not concerned about a bug in the upgrade process, I just want to make sure this server is in a healthy state.

Any suggestions appreciated.

Cheers,
Anthony

---

### Post by odin on 2008-05-14
Hi I have a similar problem. As read at ubuntu site that We should upgrade from gutsy to hardy in the server version with "do-release-upgrade" I did so but no luck.

I get the following message:


:/etc/apt# do-release-upgrade
Checking for a new ubuntu release
No new release found


I've tried with synaptic and it says that my system is up to date but nothing about upgrading.
I guessed I had to change repos in sources.list to the hardy repos but I get the same message.

So really stucked.

Any idea?

PD: before the "do-release-upgrade" I installed update-manager-core package as said in ubuntu site.

Thanks

---

