---
title: "My pam_ldap config no longer works under Hardy"
date: 2008-06-06
forum: Server Platforms
---

### Post by jaylawrence on 2008-06-06
Hi, I had a succussfully working pam_ldap under gusty. In fact I wrote the OSXLDAPClientAuthentication page in the community documentation wiki.

Anyway, with hardy we seem to have a problem. The bind is being made non-anonymously to the LDAP server. This is what I see in the "/var/log/auth.log" file

Jun  6 11:33:06 node14 sshd[6137]: pam_ldap: error trying to bind as user "uid=jay,cn=users,dc=XXX,dc=XXX,dc=XXX,dc=XX" (Invalid credentials)
Jun  6 11:33:06 node14 sshd[6137]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=192.168.3.100  user=jay
Jun  6 11:33:07 node14 sshd[6137]: Failed password for jay from 192.168.3.100 port 62825 ssh2

I've updated 

-rw-r--r-- 1 root root  423 2008-06-06 10:48 common-account
-rw-r--r-- 1 root root  531 2008-06-06 10:48 common-auth
-rw-r--r-- 1 root root 1607 2008-06-06 10:49 common-password
-rw-r--r-- 1 root root  408 2008-06-06 10:50 common-session

to resemble recommendations elsewhere

account sufficient	pam_ldap.so
account	required	pam_unix.so
auth    sufficient pam_ldap.so
auth	required	pam_unix.so nullok_secure use_first_pass
password   sufficient  pam_ldap.so
password   required    pam_unix.so nullok obscure md5 
password   optional   pam_smbpass.so nullok use_authtok use_first_pass missingok
session	required	pam_unix.so
session optional        pam_ldap.so

and my /etc/ldap.conf is same as the previous version

base cn=users,dc=XXX,dc=XXX,dc=XXX,dc=XX
host 192.168.#.#
ldap_version 3
nss_initgroups_ignoreusers backup,bin,daemon,dhcp,games,gnats,irc,klog,libuuid,list,lp,mail,man,news,proxy,root,sshd,statd,sync,sys,syslog,uucp,www-data
pam_password md5


Any ideas as to the problem or new thing I need to add?

---

### Post by jaylawrence on 2008-06-09
Fixed. I will update the Wiki. :)

---

