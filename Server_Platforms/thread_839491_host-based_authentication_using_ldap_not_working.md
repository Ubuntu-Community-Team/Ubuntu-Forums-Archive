---
title: "host-based authentication using ldap not working"
date: 2008-06-24
forum: Server Platforms
---

### Post by terencekent on 2008-06-24
Hello all,

I'm stuck attempting to get host-based access restrictions working using my ldap server. Here's what I'm working with:
> 
Ubuntu Version 8.04 (2.6.24-19-server)
ldap-utils 2.4.7
phpldapadmin 1.1.0.4


I've setup a working user/group structure per the documentation ([https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer))

I can successfully log into any system I point at the ldap server, using any ldap account. However, I can't restrict access based off of hostname. I attempted to follow the instructions on how to do this in above article, but they failed outright (schema error). So I found various articles referencing a schema extension (ldapnss.schema) that could be used in combination with some PAM configuration changes to do the trick. I was able to follow the instructions to add this schema and add the host attribute to my ldap users without errors, but access restrictions are not enforced. What's worse is I don't have any errors to work with, logins just complete successfully.

So, I'm stuck here and would like some guidance. Here are my configs on my client system:

/etc/pam.conf
> 
# ---------------------------------------------------------------------------#
# /etc/pam.conf								     #
# ---------------------------------------------------------------------------#
#
# NOTE
# ----
#
# NOTE: Most program use a file under the /etc/pam.d/ directory to setup their
# PAM service modules. This file is used only if that directory does not exist.
# ---------------------------------------------------------------------------#

# Format:
# serv.	module	   ctrl	      module [path]	...[args..]		     #
# name	type	   flag							     #

pam_check_host_attr yes
pam_filter |(host=test)(host=\*)


/etc/pam.d/common-account
> 
#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
# pre_auth-client-config # account	required	pam_unix.so
account    sufficient   pam_ldap.so
account    required     pam_unix.so


Any help would be great. As always, thanks in advance!
Terence.

---

### Post by cdenley on 2008-06-24
This is what I have for my pam configuration, which seems to work

/etc/pam.d/common-account
```

account sufficient      pam_ldap.so
account required        pam_unix.so

```
/etc/pam.d/common-auth
```

auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure

```
/etc/pam.d/common-password
```

password   sufficient   pam_ldap.so
password   required     pam_unix.so nullok obscure md5

```
/etc/pam.d/common-session
```

session required        pam_unix.so
session required        pam_mkhomedir.so skel=/etc/skel umask=0077
session optional        pam_ldap.so
session required        pam_limits.so

```

First, I think you have to install ldap-auth-config and configure /etc/ldap.conf and /etc/nsswitch.conf.

---

