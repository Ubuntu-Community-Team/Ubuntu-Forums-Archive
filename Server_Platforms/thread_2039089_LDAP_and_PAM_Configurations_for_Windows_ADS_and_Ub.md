---
title: "LDAP and PAM Configurations for Windows ADS and Ubuntu client"
date: 2012-08-08
forum: Server Platforms
---

### Post by powelltallen on 2012-08-08
Please I am having problem to login using ADS accounts on a cubox ubuntu (2.6.32.9-dove-5.4.2 #46). "getent passwd" only shows local users, however I can querry ADS users using ldapsearch command.
I have 2 systems, one that does not use gdm can login with all users (local and ADS) but the one that uses gdm allows only local users to login but not ADS users and I am getting the following error messages from /var/log/auth.log:
pam_unix(login:auth): check pass; user unknown
pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty4 ruser= rhost=
pam_unix(login:account): could not identify user (from getpwnam(gokopwin))
User not known to the underlying authentication module

On the login prompt the error says:
You must be a member of cn=ldapusers,cn=users,dc=myDomain,dc=net to login
My configuration files are:
/etc/nsswitch.conf:
passwd:         files ldap
group:          files ldap
shadow:         files ldap
hosts:          files dns mdns
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis
/etc/ldap.conf:
host MYHOSTNAME (FQ)
base dc=MYDOMAIN,dc=net
uri [ldap://SERVER.MYDOMAIN.net](ldap://SERVER.MYDOMAIN.net)
ldap_version 3
rootbinddn cn=ldap admin,cn=users,dc=MYDOMAIN,dc=net
scope sub
timelimit 30
bind_timelimit 30
bind_policy soft
idle_timelimit 3600
network timeout 20
referrals on
pam_filter objectCategory=User
pam_login_attribute sAMAccountName
pam_groupdn cn=ldapusers,cn=Users,dc=MYDOMAIN,dc=net
pam_member_attribute member
pam_password ad
nss_base_passwd dc=qcri,dc=qa?Sub?&(objectClass=User)(uidNumber=*)
nss_base_shadow dc=qcri,dc=qa?Sub?&(objectClass=User)(uidNumber=*)
nss_base_group  dc=qcri,dc=qa?Sub?&(objectClass=Group)(gidNumber=*)
nss_map_objectclass     posixAccount    User
nss_map_objectclass     shadowAccount   User
nss_map_attribute       uid             sAMAccountName
nss_map_attribute       cn              sAMAccountName
nss_map_attribute       uniqueMember    member
nss_map_attribute       homeDirectory   unixHomeDirectory
nss_map_attribute       gecos           name
nss_map_objectclass     posixGroup      Group
nss_initgroups_ignoreusers avahi,avahi-autoipd,backup,bin,bind,couchdb,daemon,dbus,games,gdm,gnats,haldaemon,hplip,irc,kernoops,ldap,libuuid,list,lp,mail,mailman,man,messagebus,myLocalUser,mysql,named,news,ntp,nz,openldap,polkituser,proxy,pulse,radiusd,radvd,root,rtkit,saned,speech-dispatcher,sshd,sync,sys,syslog,tomcat,usbmux,uucp,www-data
/etc/pam.d/*:
common-account:
ccount         sufficient      pam_ldap.so
account         required        pam_unix.so
common-auth:
auth    sufficient      pam_unix.so nullok_secure
auth    sufficient      pam_ldap.so use_first_pass
common-session:
session required pam_unix.so
session required pam_mkhomedir.so skel=/etc/skel umask=0022
common-session-noninteractive:
session required        pam_unix.so
common-password:
password        sufficient      pam_ldap.so
password        required        pam_unix.so nullok obscure md5
passwd:
@include common-password
login:
auth       optional   pam_faildelay.so  delay=3000000
auth       required  pam_securetty.so
auth       requisite  pam_nologin.so
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session       required   pam_env.so readenv=1
session       required   pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth       optional   pam_group.so
session    required   pam_limits.so
session    optional   pam_lastlog.so
session    optional   pam_motd.so
session    optional   pam_mail.so standard
@include common-account
@include common-session
@include common-password
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
gdm:
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

Any help is wellcome as I have spent almost a week on this. I thought it is simple as I succeeded in the first system, but for the cubox using gdm is proving to be a daunting task. I have google......gooogled a lot and used many materials.

Regards
Powell

---

### Post by luvshines on 2012-08-09
Since you are using pam_groupdn so the message you are seeing at the login prompt is kinda expected.

But the error you are seeing in auth.log may point to something different.

One thing I noticed is that there is a typo in your common-account pam file, a missing 'a' from account```
ccount sufficient pam_ldap.so
```
Is this typo actually there in your file on the system or was it introduced only while copying/pasting here ?

---

### Post by powelltallen on 2012-08-09
Thanks for your reply. The typo is when I copied and pasted it, I also notice that. Usually if there is a problem in the pam modules it will appear in the auth.log file. As I said, the same configuration with pam_groupdn worked fine for one of the systems (Joli OS) which is also a kind of ubuntu variant. The only difference is that the Joli OS does not use gdm while the ubuntu one that is failing uses gdm in its /etc/pam.d configuration.
 
Still working on it.....
 
Kind regards

---

