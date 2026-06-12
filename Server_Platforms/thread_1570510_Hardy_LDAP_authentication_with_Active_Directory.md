---
title: "Hardy LDAP authentication with Active Directory"
date: 2010-09-08
forum: Server Platforms
---

### Post by webbgroup on 2010-09-08
Greetings,

I have scoured the Internet, including these forums to get a Hardy ldap.conf to work with our Active Directory settings here.

We plan on using migrating NIS over to Active Directory for the short term and then migrating AD to OpenLDAP.

To do this we need to authenticate soley using LDAP, no winbind, no likewise, etc.

The problem I am receiving right now is that this line:
nss_map_objectclass posixGroup group

produces the error:
getent group
getent:/build/buildd/openldap2.3-2.4.9/libraries/libliber/sockbuf_ctrl: Assertion `sb != ((void *)0)' failed.
Aborted.

getent passwd works fine.

Below are my config settings:

common-account
account    sufficient    pam_ldap.so 
account    required    pam_unix.so try_first_pass
account    sufficient    pam_deny.so

common-auth
auth    sufficient    pam_ldap.so
auth    required    pam_unix.so nullok_secure try_first_pass

common-session
session    required    pam_unix.so
session optional    pam_ldap.so

common-passwd
password       sufficient    pam_ldap.so
password     required     pam_unix.so nullok obsecure md5

/etc/ldap.conf
base dc=sub,dc=example,dc=com
uri ldap://ldap.sub.example.com/
ldap_version 3
binddn [EMAIL="winbind_svc@sub.example.com"]winbind_svc@sub.example.com[/EMAIL]
bindpw 1alongfatpassword!
scope sub
timelimit 30
bind_timelimit 30
bind_policy soft 
pam_password md5
nss_map_objectclass posixAccount user
nss_map_objectclass shadowAccount user
nss_map_attribute uid sAMAccountName

####### Following line produces error #####
#-----> nss_map_objectclass posixGroup Group
####### Above line produces the error ####

nss_map_attribute homeDirectory unixHomeDirectory
nss_map_attribute uniqueMember member
pam_login_attribute sAMAccountName
pam_filter objectclass=User
nss_map_attribute gecos name
nss_map_attribute loginShell msSFU30loginShell
nss_map_attribute uniqueMember msSFU30PosixMember
nss_map_attribute cn sAMAccountName

ssl no
nss_initgroups_ignoreusers apache,avahi,avahi-autoipd,backup,bin,daemon,dbus,dhcp,games,gdm,gnats,haldaemon,hplip,irc,kernoops,klog,landscape,ldap,libuuid,list,lp,mail,mailman,man,messagebus,named,news,nscd,proxy,pulse,puppet,root,rtkit,saned,sftp,speech-dispatcher,sshd,statd,sync,sys,syslog,tomcat,radius,usbmux,uucp,www-data

nss_base_passwd dc=sub,dc=example,dc=com?sub
nss_base_shadow dc=sub,dc=example,dc=comsub
nss_base_group dc=sub,dc=example,dc=com?sub?&(objectCategory=group)(gidnumber=*)

---

