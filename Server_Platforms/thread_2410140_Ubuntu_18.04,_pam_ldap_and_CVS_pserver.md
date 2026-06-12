---
title: "Ubuntu 18.04, pam ldap and CVS pserver"
date: 2019-01-11
forum: Server Platforms
---

### Post by mmerlone on 2019-01-11
Hi,

I am having serious trouble to make a very plain and simple CVS pserver work with pam ldap even without chroot. SSH works fine for LDAP users, but CVS refuses to auth with error "cvs login: authorization failed: server cvs.a1.ind.br rejected access to /home/cvs for user test.account".

/etc/ldap.conf:
```
root@marte:/etc/pam.d# cat /etc/ldap.conf
base dc=blabla
host addc.blabla
ldap_version 3
binddn yyyyyyyy
bindpw xxxxxxxxx
scope sub
pam_filter objectclass=user
pam_login_attribute sAMAccountName
pam_member_attribute memberOf
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName
nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute shadowLastChange pwdLastSet
nss_map_objectclass posixGroup group
nss_map_attribute uniqueMember member
pam_login_attribute sAMAccountName
pam_filter objectclass=User
pam_password ad
nss_initgroups_ignoreusers avahi,backup,bacula,bin,bind,clamav,daemon,dovecot,games,gnats,irc,landscape,libuuid,list,logcheck,lp,mail,man,messagebus,munin,mysql,news,ntp,openfire,postfix,proxy,root,snmp,sshd,statd,sync,sys,syslog,uucp,www-data
root@marte:/etc/pam.d# 
```

/etc/nsswitch.conf:
```
root@marte:/etc/pam.d# grep -v "^\s*#\|^\s*$" /etc/nsswitch.conf 
passwd:         compat ldap
group:          compat ldap
shadow:     compat
hosts:          files dns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
sudoers                 files
root@marte:/etc/pam.d# 
```

/etc/cvsd/cvsd.conf:
```
root@marte:/etc/pam.d# grep -v "^\s*#\|^\s*$" /etc/cvsd/cvsd.conf
RootJail none
Uid root
Gid cvsd
Nice 1
Umask 007
PidFile /var/run/cvsd.pid
MaxConnections 10
Log /var/log/cvsd.log debug
Listen * 2401
Repos /home/cvs
root@marte:/etc/pam.d#
``` 

Tried with and without this /etc/pam.d/cvs :
```
root@marte:/etc/pam.d# grep -v "^\s*#\|^\s*$" /etc/pam.d/cvs 
@include common-auth
@include common-account
root@marte:/etc/pam.d# 
```

Login attempt:

```
root@marte:/etc/pam.d# cvs -t -d :pserver:test.account@cvs.a1.ind.br:2401/home/cvs login
  -> main: Session ID is 1005C3898BC15FAE8C7
  -> main loop with CVSROOT=/home/cvs
Logging in to :pserver:test.account@cvs.a1.ind.br:2401/home/cvs
CVS password: 
  -> Connecting to cvs.a1.ind.br(10.9.8.7):2401.
cvs login: authorization failed: server cvs.a1.ind.br rejected access to /home/cvs for user test.account
root@marte:/etc/pam.d# 
```

/var/log/auth.log:
```
Jan 11 10:49:58 marte cvs: password mismatch for test.account: * vs. x
Jan 11 10:49:58 marte cvs: login refused for test.account: user has no password
```

/var/log/daemon.log:
```
Jan 11 10:49:58 marte cvs: login failure (for /home/cvs)
```

Searched Google but no luck, only old posts with o solution for my situation. Can anybody please help?

Thanks in advance, best regards.

---

