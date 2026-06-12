---
title: "Ubuntu 12.04 Preseed LDAP Config"
date: 2013-10-21
forum: Server Platforms
---

### Post by Artur0ide on 2013-10-21
Hi!

I'm trying to deploy Ubuntu 12.04 via xCAT, everything works except the automatic configuration of LDAP, the preseed file is read but the file /etc/nsswitch is not written properly.

My Preseed File:

[...]
### LDAP Setup
nslcd   nslcd/ldap-bindpw    password
ldap-auth-config        ldap-auth-config/bindpw password
ldap-auth-config        ldap-auth-config/rootbindpw     password
ldap-auth-config        ldap-auth-config/binddn string  cn=proxyuser,dc=example,dc=net
libpam-runtime  libpam-runtime/profiles multiselect     unix, ldap, gnome-keyring, consolekit, capability
ldap-auth-config        ldap-auth-config/dbrootlogin    boolean false
ldap-auth-config        ldap-auth-config/rootbinddn     string  cn=manager,dc=xcat-domain,dc=com
nslcd   nslcd/ldap-starttls     boolean false
nslcd   nslcd/ldap-base string  dc=xcat-domain,dc=com
ldap-auth-config        ldap-auth-config/pam_password   select  md5
ldap-auth-config        ldap-auth-config/move-to-debconf        boolean true
ldap-auth-config        ldap-auth-config/ldapns/ldap-server     string  ldap://192.168.32.42
ldap-auth-config        ldap-auth-config/ldapns/base-dn string  dc=xcat-domain,dc=com
ldap-auth-config        ldap-auth-config/override    boolean true

libnss-ldapd    libnss-ldapd/clean_nsswitch     boolean false
libnss-ldapd    libnss-ldapd/nsswitch   multiselect     passwd,group,shadow
nslcd   nslcd/ldap-reqcert    select
ldap-auth-config        ldap-auth-config/ldapns/ldap_version    select  3
ldap-auth-config        ldap-auth-config/dblogin        boolean false

nslcd   nslcd/ldap-uris string  ldap://192.168.32.42
nslcd   nslcd/ldap-binddn    string

[...]

After the installation, nsswitch.conf rimains unchanged.




   Has someone an idea??

Thanks!

---

