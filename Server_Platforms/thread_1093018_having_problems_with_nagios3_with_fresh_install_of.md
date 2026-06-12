---
title: "having problems with nagios3 with fresh install of ubuntu 8.10 server"
date: 2009-03-11
forum: Server Platforms
---

### Post by kustomjs on 2009-03-11
Hi Guys
when I tried to install nagios3 onto my fresh ubuntu 8.10 server I get these error messages:
```
Setting up libsensors3 (1:2.10.7-1) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `i2c-0-': Read-only file system
mknod: `i2c-0-': Read-only file system
makedev i2c-0 c 89 0 root root 0600: failed
rm: cannot remove `i2c-0-': Read-only file system
rm: cannot remove `i2c-1-': Read-only file system
mknod: `i2c-1-': Read-only file system
makedev i2c-1 c 89 1 root root 0600: failed
rm: cannot remove `i2c-1-': Read-only file system
rm: cannot remove `i2c-2-': Read-only file system
mknod: `i2c-2-': Read-only file system
makedev i2c-2 c 89 2 root root 0600: failed
rm: cannot remove `i2c-2-': Read-only file system
rm: cannot remove `i2c-3-': Read-only file system
mknod: `i2c-3-': Read-only file system
makedev i2c-3 c 89 3 root root 0600: failed
rm: cannot remove `i2c-3-': Read-only file system
rm: cannot remove `i2c-4-': Read-only file system
mknod: `i2c-4-': Read-only file system
makedev i2c-4 c 89 4 root root 0600: failed
rm: cannot remove `i2c-4-': Read-only file system
rm: cannot remove `i2c-5-': Read-only file system
mknod: `i2c-5-': Read-only file system
makedev i2c-5 c 89 5 root root 0600: failed
rm: cannot remove `i2c-5-': Read-only file system
rm: cannot remove `i2c-6-': Read-only file system
mknod: `i2c-6-': Read-only file system
makedev i2c-6 c 89 6 root root 0600: failed
rm: cannot remove `i2c-6-': Read-only file system
rm: cannot remove `i2c-7-': Read-only file system
mknod: `i2c-7-': Read-only file system
makedev i2c-7 c 89 7 root root 0600: failed
rm: cannot remove `i2c-7-': Read-only file system

Setting up libsnmp-base (5.4.1~dfsg-7.1ubuntu6.1) ...
Setting up libsnmp15 (5.4.1~dfsg-7.1ubuntu6.1) ...

Setting up libtalloc1 (1.2.0~git20080616-1) ...

Setting up libwbclient0 (2:3.2.3-1ubuntu3.4) ...

Setting up nagios-images (0.4) ...
Setting up nagios-plugins-basic (1.4.11-2ubuntu2.1) ...
Not replacing deleted config file /etc/nagios-plugins/config/apt.cfg
Not replacing deleted config file /etc/nagios-plugins/config/dhcp.cfg
Not replacing deleted config file /etc/nagios-plugins/config/disk.cfg
Not replacing deleted config file /etc/nagios-plugins/config/dummy.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ftp.cfg
Not replacing deleted config file /etc/nagios-plugins/config/http.cfg
Not replacing deleted config file /etc/nagios-plugins/config/load.cfg
Not replacing deleted config file /etc/nagios-plugins/config/mail.cfg
Not replacing deleted config file /etc/nagios-plugins/config/news.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ntp.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ping.cfg
Not replacing deleted config file /etc/nagios-plugins/config/procs.cfg
Not replacing deleted config file /etc/nagios-plugins/config/real.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ssh.cfg
Not replacing deleted config file /etc/nagios-plugins/config/tcp_udp.cfg
Not replacing deleted config file /etc/nagios-plugins/config/telnet.cfg
Not replacing deleted config file /etc/nagios-plugins/config/users.cfg

Setting up nagios3-doc (3.0.2-1ubuntu1.1) ...

Setting up nagios3-common (3.0.2-1ubuntu1.1) ...
Not replacing deleted config file /etc/nagios3/apache2.conf
Not replacing deleted config file /etc/nagios3/conf.d/host-gateway_nagios3.cfg
include file /etc/nagios3/apache2.conf does not exist!
dpkg: error processing nagios3-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nagios3:
 nagios3 depends on nagios3-common (= 3.0.2-1ubuntu1.1); however:
  Package nagios3-common is not configured yet.
dpkg: error processing nagios3 (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.2.3-1ubuntu3.4) ...
No apport report written because the error message indicates its a followup error from a previous failure.

Setting up smbclient (2:3.2.3-1ubuntu3.4) ...
Setting up snmp (5.4.1~dfsg-7.1ubuntu6.1) ...
Setting up libradius1 (0.3.2-11.1) ...

Setting up radiusclient1 (0.3.2-11.1) ...
Setting up nagios-plugins-standard (1.4.11-2ubuntu2.1) ...
Not replacing deleted config file /etc/nagios-plugins/config/breeze.cfg
Not replacing deleted config file /etc/nagios-plugins/config/disk-smb.cfg
Not replacing deleted config file /etc/nagios-plugins/config/dns.cfg
^ANot replacing deleted config file /etc/nagios-plugins/config/flexlm.cfg
Not replacing deleted config file /etc/nagios-plugins/config/hppjd.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ifstatus.cfg
Not replacing deleted config file /etc/nagios-plugins/config/ldap.cfg
Not replacing deleted config file /etc/nagios-plugins/config/mrtg.cfg
Not replacing deleted config file /etc/nagios-plugins/config/mysql.cfg
Not replacing deleted config file /etc/nagios-plugins/config/netware.cfg
Not replacing deleted config file /etc/nagios-plugins/config/nt.cfg
Not replacing deleted config file /etc/nagios-plugins/config/pgsql.cfg
Not replacing deleted config file /etc/nagios-plugins/config/radius.cfg
Not replacing deleted config file /etc/nagios-plugins/config/rpc-nfs.cfg
Not replacing deleted config file /etc/nagios-plugins/config/snmp.cfg
Not replacing deleted config file /etc/nagios-plugins/config/vsz.cfg

Setting up nagios-plugins (1.4.11-2ubuntu2.1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nagios3-common
 nagios3
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by kustomjs on 2009-03-11
can anybody please help?

---

### Post by kustomjs on 2009-03-11
can somebody please help I need this fix Soon As Possible. Thanks

---

### Post by kustomjs on 2009-03-12
I will keep bumping this post intill somebody takes little bit of there time and help me with my error. Thanks

---

### Post by kustomjs on 2009-03-13
back on top again.

---

### Post by kustomjs on 2009-03-14
back on top again.

---

### Post by kustomjs on 2009-03-15
alright piss on this I will just reinstall fresh copy of Ubuntu since Im not getting any help on this issue.

---

### Post by Vico Vicario on 2009-03-18
1)

Uninstall & **purge** all nagios packages. Purging deletes the configuration files. You can use synaptic to purge completely.

Then try to reinstall. This should work for all sane packages.

2)

If it fails again then it is a bug with nagios and you need to:

Uninstall & **purge** all nagios packages. 

Then manually do:

ucf --purge <filename>

where <filename> is the complete filename for each of the files that says "Not replacing deleted config file ...".

Then reinstall nagios packages.

V.

---

