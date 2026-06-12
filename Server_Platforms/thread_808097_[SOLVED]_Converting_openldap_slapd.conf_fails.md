---
title: "[SOLVED] Converting openldap slapd.conf fails"
date: 2008-05-26
forum: Server Platforms
---

### Post by Paindistributor on 2008-05-26
I'm currently preparing a openldap server for my needs and i thought using the dynamic configuration is a good idea - wrong! :evil:
Everytime i want to convert my slapd.conf it fails with that "Permission denied" failure:

```
$ sudo /usr/sbin/slapd -u openldap -g openldap -f /etc/ldap/slapd.conf -F /etc/ldap/slapd.d
```

Syslog says:

```
May 26 16:54:39 ubuntu-vbox slapd[6768]: @(#) $OpenLDAP: slapd 2.4.7 (Apr 29 2008 08:44:27) $ ^Ibuildd@rothera:/build/buildd/openldap2.3-2.4.7/debian/build/servers/slapd 
May 26 16:54:39 ubuntu-vbox slapd[6769]: could not create tmpfile "/etc/ldap/slapd.d/cn=config.ldifTENT6k": Permission denied 
May 26 16:54:39 ubuntu-vbox slapd[6769]: backend_startup_one: bi_db_open failed! (-1) 
May 26 16:54:39 ubuntu-vbox slapd[6769]: slapd stopped. 
May 26 16:54:39 ubuntu-vbox slapd[6769]: connections_destroy: nothing to destroy. 
May 26 16:54:39 ubuntu-vbox kernel: [ 6966.472787] audit(1211813679.024:33): type=1503 operation="inode_create" requested_mask="w::" denied_mask="w::" name="/etc/ldap/slapd.d/cn=config.ldifTENT6k" pid=6769 profile="/usr/sbin/slapd" namespace="default"
```

The directory "/etc/ldap/slapd.d" has owner and group "openldap" with all access rights (rwx).

I tried to process that as root, changed the access rights all to 777 or even used another directory for output - without any success.
Slapd is completely fresh installed without any changes. I tried the same procedure on my debian box that had working fine for me.
The question is, where's the access problem?

The OS is Ubuntu 8.04 desktop running within virtualbox. I hope someone got this up and running ](*,)

---

### Post by windependence on 2008-05-26
Make sure the ownership and permissions on the slap.d directory are set recursively so that when the temp directory is created it has the same permissions and ownership as the parent directory.

-Tim

---

### Post by Paindistributor on 2008-05-26
I finally found the answer. #-o
In order to get slapd work, apparmor has to be configured properly.
It came me in mind after rethinking about my problem.

All to do is follwing:

1. Add the slapd.d directory to the access-list in file "/etc/apparmor.d/usr.sbin.slapd"

```
/etc/ldap/slapd.d/* rw,
```

2. Restart apparmor

```
$ sudo /etc/init.d/apparmor restart
```

3. Stop slapd

```
$ sudo /etc/init.d/slapd stop
```

4. Convert the slapd configuration

```
sudo /usr/sbin/slapd -u openldap -g openldap -f /etc/ldap/slapd.conf -F /etc/ldap/slapd.d
```

5. Start slapd

```
$ sudo /etc/init.d/slapd start
```

After that, all should be fine:

```
user@ubuntu-vbox:/etc$ sudo ls -l ldap/slapd.d/
[sudo] password for user: 
insgesamt 4
-rw------- 1 openldap openldap 977 2008-05-26 18:00 cn=config.ldif

```

The last important thing is not forget to set the rights in 
apparmor to a safer setting (and restart apparmor):

```
/etc/ldap/slapd.d/* r,
```

That's exactly that i wanted to do. Apparmor tricked me out here,
but did the right thing for security reasons.

Thanks for your help

Happy end :rolleyes:

---

