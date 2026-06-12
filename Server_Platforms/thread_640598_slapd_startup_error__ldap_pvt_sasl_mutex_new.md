---
title: "slapd startup error  ldap_pvt_sasl_mutex_new"
date: 2007-12-14
forum: Server Platforms
---

### Post by mbradlcu on 2007-12-14
Hi all,
I'm not sure if it was an upgrade but slapd won't start. 
I've purged slapd and reinstalled and tried starting it with stock slapd.conf
I'm using 7.10x86 btw

> 
root@mattx64:/etc/ldap# /usr/sbin/slapd -d 255
@(#) $OpenLDAP: slapd 2.3.35 (Dec  3 2007 20:02:39) $
        buildd@terranova:/build/buildd/openldap2.3-2.3.35/debian/build/servers/slapd
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: listener initialized ldap:///
daemon_init: 2 listeners opened
slapd init: initiated server.
/usr/sbin/slapd: symbol lookup error: /usr/sbin/slapd: undefined symbol: ldap_pvt_sasl_mutex_new


thanks in advance!

---

### Post by mbradlcu on 2007-12-14
ok, here's a fix, although it may break stuff..
when in /usr/local/lib I created a dir ZZZborked then:
```

mv libldap* ZZZborked/

```
and then for kicks ran ldconfig

it was a very uneducated guess but slapd starts. I compared /usr/local/lib to another machine that installed and ran slapd without issue. 

If anyone would like the enlighten me on why this fixed the issue I'd greatly appreciate it!

thanks

---

### Post by mbradlcu on 2007-12-14
seems the upgrade also fails on 6.10 server too but not as seriously,,
QnDirty, it seems slapd should be stopped before upgrading, below is the resolve path:

> 
Setting up slapd (2.2.26-5ubuntu2.4) ...
  Backing up /etc/ldap/slapd.conf in /var/backups/slapd-2.2.26-5ubuntu2.2... don
e.
Starting OpenLDAP: (slapd running, no recovery),  slapd - failed.
The operation failed but no output was produced. For hints on what went
wrong please refer to the system's logfiles (e.g. /var/log/syslog) or
try running the daemon in Debug mode like via "slapd -d 16383" (warning:
this will create copious output).
invoke-rc.d: initscript slapd, action "start" failed.
dpkg: error processing slapd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 slapd
E: Sub-process /usr/bin/dpkg returned an error code (1)


here's the debug
> 
root@portal:/usr/local/lib# slapd -d 16383
@(#) $OpenLDAP: slapd 2.2.26 (Dec  3 2007 20:22:15) $
        buildd@terranova:/build/buildd/openldap2.2-2.2.26/debian/build/servers/s
lapd
daemon_init: <null>
daemon_init: listen on ldap:///
daemon_init: 1 listeners to open...
ldap_url_parse_ext(ldap:///)
daemon: bind(6) failed errno=98 (Address already in use)
daemon: bind(6) failed errno=98 (Address already in use)
slap_open_listener: failed on ldap:///
slapd stopped.
connections_destroy: nothing to destroy.


oops seems it still running, so:
```

/etc/init.d/slapd restart

```

and phinally!
```

apt-get update

```
> 
Setting up slapd (2.2.26-5ubuntu2.4) ...
  Backi[ng up /etc/ldap/slapd.conf in /var/backups/slapd-2.2.26-5ubuntu2.2... done
e.
Starting OpenLDAP: (slapd running, no recovery),  slapd.


To whom it may concern, openldap is a critical system for us, and over the past couple years there's been several show stopping issues that have occurred centric to the very fine Ubuntu distro. If anyone can let me know how I could assist in QA I'd be very happy to help out!

---

