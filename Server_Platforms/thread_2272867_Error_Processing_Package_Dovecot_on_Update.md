---
title: "Error Processing Package Dovecot on Update"
date: 2015-04-09
forum: Server Platforms
---

### Post by damo12 on 2015-04-09
Hi,

I am running a headless server running Ubuntu 14.04.02 accessed through Putty and Webmin.  This server originally ran 10.04 and was upgraded to 12.04 and finally 14.04.

When I logged on I received a message saying that there were packages that needed updating.  I was surprised at this as my "*/etc/apt/apt.conf.d/50unattended-upgrades*" reads:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
        "${distro_id}:${distro_codename}-security";
        "${distro_id}:${distro_codename}-updates";
//      "${distro_id}:${distro_codename}-proposed";
//      "${distro_id}:${distro_codename}-backports";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};
```


When I ran the commands:
```
sudo apt-get update
sudo apt-get upgrade
```

I received the following error message:
```
********************:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-46 linux-headers-3.13.0-46-generic
  linux-image-3.13.0-46-generic linux-image-extra-3.13.0-46-generic
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-headers-server linux-image-generic
  linux-image-server linux-server
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up dovecot-core (1:2.2.9-1ubuntu2.1) ...
You already have ssl certs for dovecot.
However you should move them out of /etc/ssl
and into /etc/dovecot and update the configuration
in /etc/dovecot/conf.d/10-ssl.conf accordingly.
See /usr/share/doc/dovecot-core/README.Debian.gz for details.
You already have ssl certs for dovecot.
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 102
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-core (= 1:2.2.9-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-core (= 1:2.2.9-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-core
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Following the instructions, I tried running:
```
sudo apt-get autoremove
```


This runs for some time giving a long output which finishes with:
```
Setting up dovecot-core (1:2.2.9-1ubuntu2.1) ...
You already have ssl certs for dovecot.
However you should move them out of /etc/ssl
and into /etc/dovecot and update the configuration
in /etc/dovecot/conf.d/10-ssl.conf accordingly.
See /usr/share/doc/dovecot-core/README.Debian.gz for details.
You already have ssl certs for dovecot.
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 102
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I understand that this is a problem with dovecot, I have tried removing it using the command:
```
sudo apt-get remove dovecot
```


But I received the following output:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'dovecot' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up dovecot-core (1:2.2.9-1ubuntu2.1) ...
You already have ssl certs for dovecot.
However you should move them out of /etc/ssl
and into /etc/dovecot and update the configuration
in /etc/dovecot/conf.d/10-ssl.conf accordingly.
See /usr/share/doc/dovecot-core/README.Debian.gz for details.
You already have ssl certs for dovecot.
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error processing package dovecot-core (--configure):
 subprocess installed post-installation script returned error exit status 102
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-core (= 1:2.2.9-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            dpkg: error processing package dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-core (= 1:2.2.9-1ubuntu2.1); however:
  Package dovecot-core is not configured yet.

dpkg: error processing package dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            Errors were encountered while processing:
 dovecot-core
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Can you please tell me where I am going wrong?

Thanks

---

### Post by SeijiSensei on 2015-04-09
Try removing "dovecot-core" and see if that helps.  The easiest method is to run
```
sudo apt-get remove dovecot-* --purge
```
There are about a dozen related packages to dovecot, all named "dovecot-something" like "dovecot-imapd".

---

### Post by damo12 on 2015-04-09
I tried running "*sudo apt-get remove dovecot-* --purge*" and received this output:
```
***************:~$ sudo apt-get remove dovecot-* --purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting 'dovecot-metadata-plugin' for regex 'dovecot-*'
Note, selecting 'mysqmail-dovecot-logger' for regex 'dovecot-*'
Note, selecting 'dovecot-pgsql' for regex 'dovecot-*'
Note, selecting 'dovecot-sieve' for regex 'dovecot-*'
Note, selecting 'dovecot-sqlite' for regex 'dovecot-*'
Note, selecting 'dovecot-ldap' for regex 'dovecot-*'
Note, selecting 'dovecot-dbg' for regex 'dovecot-*'
Note, selecting 'dovecot-managesieved' for regex 'dovecot-*'
Note, selecting 'dovecot-dev' for regex 'dovecot-*'
Note, selecting 'dovecot-gssapi' for regex 'dovecot-*'
Note, selecting 'dovecot-common' for regex 'dovecot-*'
Note, selecting 'dovecot-mysql' for regex 'dovecot-*'
Note, selecting 'dovecot-core' for regex 'dovecot-*'
Note, selecting 'dovecot-solr' for regex 'dovecot-*'
Note, selecting 'dovecot-lmtpd' for regex 'dovecot-*'
Note, selecting 'dovecot-pop3d' for regex 'dovecot-*'
Note, selecting 'dovecot' for regex 'dovecot-*'
Note, selecting 'dovecot-imapd' for regex 'dovecot-*'
Note, selecting 'dovecot-antispam' for regex 'dovecot-*'
Note, selecting 'dovecot-postfix' for regex 'dovecot-*'
Note, selecting 'dovecot-core' instead of 'dovecot-common'
Package 'dovecot-postfix' is not installed, so not removed
Package 'dovecot' is not installed, so not removed
Package 'dovecot-antispam' is not installed, so not removed
Package 'dovecot-metadata-plugin' is not installed, so not removed
Package 'mysqmail-dovecot-logger' is not installed, so not removed
Package 'dovecot-dbg' is not installed, so not removed
Package 'dovecot-dev' is not installed, so not removed
Package 'dovecot-imapd' is not installed, so not removed
Package 'dovecot-managesieved' is not installed, so not removed
Package 'dovecot-pop3d' is not installed, so not removed
Package 'dovecot-sieve' is not installed, so not removed
Package 'dovecot-gssapi' is not installed, so not removed
Package 'dovecot-ldap' is not installed, so not removed
Package 'dovecot-lmtpd' is not installed, so not removed
Package 'dovecot-mysql' is not installed, so not removed
Package 'dovecot-pgsql' is not installed, so not removed
Package 'dovecot-solr' is not installed, so not removed
Package 'dovecot-sqlite' is not installed, so not removed
The following packages will be REMOVED
  dovecot-core*
0 to upgrade, 0 to newly install, 1 to remove and 6 not to upgrade.
1 not fully installed or removed.
After this operation, 6,833 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1072914 files and directories currently installed.)
Removing dovecot-core (1:2.2.9-1ubuntu2.1) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error processing package dovecot-core (--purge):
 subprocess installed pre-removal script returned error exit status 102
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 102
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


As the problem seems to be with "[I]dovecot-core[I]" I tried running
```
sudo apt-get remove dovecot-core
```

but received the output:
```
***************:~$:~$ sudo apt-get remove dovecot-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  dovecot-core
0 to upgrade, 0 to newly install, 1 to remove and 6 not to upgrade.
1 not fully installed or removed.
After this operation, 6,833 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1072914 files and directories currently installed.)
Removing dovecot-core (1:2.2.9-1ubuntu2.1) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error processing package dovecot-core (--remove):
 subprocess installed pre-removal script returned error exit status 102
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 102
Errors were encountered while processing:
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


I tried rebooting the server and running these commands again but I still received the same output.

---

### Post by SeijiSensei on 2015-04-09
```
invoke-rc.d: dangling symlink: /etc/rc2.d/S24dovecot
```

Look in the directory /etc/rc2.d and see if there is a symbolic link named "S24dovecot".  If so, delete it with "sudo rm -f S24dovecot", then try purging dovecot-core again:
```

cd /etc/rc2.d
ls | grep dovecot
[if "S24dovecot" is returned] 
sudo rm -f S24dovecot
sudo apt-get remove --purge dovecot-core

```
S24dovecot is a symbolic link to /etc/init.d/dovecot, the script that starts the Dovecot mail server.  You might have removed the script itself but accidentally left the symlink behind so it is "dangling."  It would be nice if the installer handled this better.

---

### Post by damo12 on 2015-04-09
Thanks for the help SeijiSensei, that worked perfectly.

---

### Post by SeijiSensei on 2015-04-09
You're welcome.  I don't know why the packager cares about the symlink.  If the installer finds a "dangling" one, it should just delete it and continue on.  Presenting an obscure error message to the user seems unhelpful.

---

