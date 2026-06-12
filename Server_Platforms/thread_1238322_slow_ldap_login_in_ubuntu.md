---
title: "slow ldap login in ubuntu"
date: 2009-08-12
forum: Server Platforms
---

### Post by snopyland on 2009-08-12
Hi,
 
I have a Novell ldap server (ldap vers 3)and I need to configure ubuntu 9.04 to authenticate against the ldap server (i.e. to do ldap login in ubuntu). I find that the ldap login in ubuntu is slow. 
If I remove the "ldap" in the group entry of /etc/nsswitch.conf (as show below), the ldap login is fast and back to normal.
 
In the auth.log, it shows 
Jul 31 17:13:02 server1 login[26282]: pam_unix(login:auth): authentication failu
re; logname=test1 uid=0 euid=0 tty=tty1 ruser= rhost=  user=test1
Jul 31 17:13:23 server1 login[26282]: nss_ldap: could not get LDAP result - Time
d out
Jul 31 17:13:43 server1 login[26282]: pam_unix(login:session): session opened fo
r user test1 by test1(uid=0)
 
Anyone can give me some hints on this?  Below is my configuration.
 
nsswitch.conf
-------------------
passwd: files ldap
group: files ldap  <--- remove "ldap" here
shadow: files ldap
hosts: files dns
networks: files
protocols: db files
services: db files
ethers: db files
rpc: db files
netgroup: nis
 ldap.conf
 ------------
host    ldapserver
base    o=mycom
ldap_version    3
scope   sub
timelimit       20
pam_login_attribute     uid
binddn  uid=admin,o=mycom
bindpw  adminpasswd
pam_filter      objectclass=posixAccount
bind_policy soft
pam_member_attribute uniqueMember
 
common-auth
-------------------
auth required /lib/security/pam_env.so
auth sufficient /lib/security/pam_unix.so likeauth nullok
auth sufficient /lib/security/pam_ldap.so try_first_pass
auth required /lib/security/pam_deny.so
 common-account
-------------------------
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 default=ignore]      pam_ldap.so
account requisite                       pam_deny.so
account required                        pam_permit.so
 
common-password
---------------------------
password required /lib/security/pam_cracklib.so retry=3 type=
password sufficient /lib/security/pam_unix.so nullok use_authtok md5 shadow
password sufficient /lib/security/pam_ldap.so use_authtok
password required /lib/security/pam_deny.so
 
common-sessions
-------------------------
session required /lib/security/pam_limits.so
session required /lib/security/pam_unix.so
session optional /lib/security/pam_ldap.so
 
 
Any comments are appreciated.
 
Thanks

---

### Post by snopyland on 2009-08-12
Hi,
 
I have a Novell ldap server (ldap vers 3)and I need to configure ubuntu 9.04 to authenticate against the ldap server (i.e. to do ldap login in ubuntu). I find that the ldap login in ubuntu is slow. 
If I remove the "ldap" in the group entry of /etc/nsswitch.conf (as show below), the ldap login is fast and back to normal.
 
In the auth.log, it shows 
Jul 31 17:13:02 server1 login[26282]: pam_unix(login:auth): authentication failu
re; logname=test1 uid=0 euid=0 tty=tty1 ruser= rhost=  user=test1
Jul 31 17:13:23 server1 login[26282]: nss_ldap: could not get LDAP result - Time
d out
Jul 31 17:13:43 server1 login[26282]: pam_unix(login:session): session opened fo
r user test1 by test1(uid=0)
 
Anyone can give me some hints on this?  Below is my configuration.
 
nsswitch.conf
-------------------
passwd: files ldap
group: files ldap  <--- remove "ldap" here
shadow: files ldap
hosts: files dns
networks: files
protocols: db files
services: db files
ethers: db files
rpc: db files
netgroup: nis
 ldap.conf
 ------------
host    ldapserver
base    o=mycom
ldap_version    3
scope   sub
timelimit       20
pam_login_attribute     uid
binddn  uid=admin,o=mycom
bindpw  adminpasswd
pam_filter      objectclass=posixAccount
bind_policy soft
pam_member_attribute uniqueMember
 
common-auth
-------------------
auth required /lib/security/pam_env.so
auth sufficient /lib/security/pam_unix.so likeauth nullok
auth sufficient /lib/security/pam_ldap.so try_first_pass
auth required /lib/security/pam_deny.so
 common-account
-------------------------
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 default=ignore]      pam_ldap.so
account requisite                       pam_deny.so
account required                        pam_permit.so
 
common-password
---------------------------
password required /lib/security/pam_cracklib.so retry=3 type=
password sufficient /lib/security/pam_unix.so nullok use_authtok md5 shadow
password sufficient /lib/security/pam_ldap.so use_authtok
password required /lib/security/pam_deny.so
 
common-sessions
-------------------------
session required /lib/security/pam_limits.so
session required /lib/security/pam_unix.so
session optional /lib/security/pam_ldap.so
 
 
Any comments are appreciated.
 
Thanks

---

### Post by cariboo on 2009-08-12
Merged two threads.

---

### Post by Mr-Manor on 2010-08-12
Hi snopyland

I'v just been hit by this bug. Did you manage to find a solution?

If not please consider to vote for [Bug 616719]("https://bugs.launchpad.net/ubuntu/+source/libnss-ldap/+bug/616719")

---

