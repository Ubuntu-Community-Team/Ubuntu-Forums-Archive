---
title: "Pure-FTPD LDAP Fails with SSL Enabled"
date: 2013-11-04
forum: Server Platforms
---

### Post by sandyd on 2013-11-04
I currently have a pure-ftpd-ldap server with the configuration below

```

#############################################
#                                           #
# Sample Pure-FTPd LDAP configuration file. #
# See README.LDAP for explanations.         #
#                                           #
#############################################


#LDAPScheme  ldaps
# Optional : name of the LDAP server. Default : localhost

LDAPServer ldap.sandydprod.net


# Optional : server port. Default : 389

LDAPPort   636
#LDAPPort        389
#LDAPScheme ldaps
# Mandatory : the base DN to search accounts from. No default.

LDAPBaseDN  <removed>


# Optional : who we should bind the server as.
#            Default : binds anonymously or binds as FTP users

LDAPBindDN <removed>


# Password if we don't bind anonymously
# This configuration file should be only readable by root

LDAPBindPW <removed>


# Optional : default UID, when there's no entry in a user object

# LDAPDefaultUID 500


# Optional : default GID, when there's no entry in a user object

# LDAPDefaultGID 100


# Filter to use to find the object that contains user info
# \L is replaced by the login the user is trying to log in as
# The default filter is (&(objectClass=posixAccount)(uid=\L))

LDAPFilter (&(objectClass=PureFTPdUser)(uid=\L))


# Attribute to get the home directory
# Default is homeDirectory (the standard attribute from posixAccount)

#LDAPHomeDir homeDirectory


# LDAP protocol version to use
# Version 3 (default) is mandatory with recent releases of OpenLDAP.

LDAPVersion 3


# Optional: use TLS to connect to the LDAP server
LDAPUseTLS  True


# Can be PASSWORD or BIND.
# PASSWORD retrieves objects and checks against the userPassword attribute
# BIND tries to bind

LDAPAuthMethod BIND


# Optional: default home directory if there's LDAPHomeDir entry

# LDAPDefaultHomeDirectory /var/shared
```

Somehow, if I set LDAP to use TLS auth instead of cleartext, it fails to authenticate. Is TLS the same as SSL in pure-ftpd-ldap? Or does it even matter?

Here is a (working) nslcd.conf that I have been using on the same computer
```

# /etc/nslcd.conf
# nslcd configuration file. See nslcd.conf(5)
# for details.

# The user and group nslcd should run as.
uid nslcd
gid nslcd

# The location at which the LDAP server(s) should be reachable.
uri ldaps://ldap.sandydprod.net

# The search base that will be used for all queries.
base dc=sandydprod,dc=net

# The LDAP protocol version to use.
#ldap_version 3

# The DN to bind with for normal lookups.
binddn <removed>
bindpw <removed>

# The DN used for password modifications by root.
#rootpwmoddn cn=admin,dc=example,dc=com

# SSL options
ssl on
tls_reqcert demand

# The search scope.
#scope sub

#nss_base_passwd DC=sandydpnet,DC=me?one?gidNumber=1002
#filter passwd (gidNumber=1002)
#tls_cacertdir /etc/ssl/globalsign/
tls_cacert /etc/ssl/globalsign/ca.crt
```
I have specified 
```

tls_cacert /etc/ssl/globalsign/ca.crt
```
in /etc/ldap/ldap.conf as well.

Thanks!

---

