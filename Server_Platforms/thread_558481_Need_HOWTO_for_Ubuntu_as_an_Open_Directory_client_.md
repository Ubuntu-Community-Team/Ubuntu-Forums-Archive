---
title: "Need HOWTO for Ubuntu as an Open Directory client (LDAP/Kerberos/XServe)"
date: 2007-09-24
forum: Server Platforms
---

### Post by jbronson on 2007-09-24
Hi All,

I've been banging my head against Ubuntu's LDAP/Kerberos configuration off and on for almost half the summer, and I'm hoping there's a definitive HOWTO out there, or at least someone who can spell it out clearly.  There's plenty of guides to LDAP on Active Directory, but none that work for OD.  Other Linux distros (Fedora especially) have simple tools to enable LDAP/Kerberos with a checkbox and entering a realm, but I still can't get Ubuntu to behave as smoothly.

I'd like the Ubuntu clients to behave as close to OS X clients as possible:

-Login with LDAP or local account (local account overrides network account with same name)
-Kerberos auth (TGT) for login and network services
-Network-mounted home directory (same as their OS X home dir)
-Optional auto-mount of shared NFS volume

The standard LDAP/Kerberos packages have been installed, and the ldap.conf and krb5.conf files are sorted out.  LDAP can see the networked users when using 'getent passwd', and Kerberos has a host keytab and can request a ticket-granting ticket.  However, editing the PAM files as instructed in the guides I've seen caused Ubuntu to ask for passwords twice during login and with things like sudo, but would not accept network authentication.

I hope someone with direct experience can help out with this, or at least point me in the direction of some definitive instructions.  Thanks!

---

### Post by elvis on 2007-09-24
> **jbronson said:**
>  I've seen caused Ubuntu to ask for passwords twice during login and with things like sudo, but would not accept network authentication.

PAM by default will try each of the authentication methods you've defined in the /etc/pam.d/common-* files.  For example, my common-password file looks like:

```
password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5
```

So when logging in via an account that is an LDAP uid, everything works well (PAM asks LDAP first, and if the account exists, allows login).  However if the account is local (a password stored in /etc/passwd, such as "root"), it asks for the password twice.

What you need to do is to tell all the PAM modules that in the event of a failure, they should hold onto the previous password and try it against the next module.. To do so, add the "use_first_pass" flag as such:

```
password   sufficient   pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5 use_first_pass
```

And the same in common-auth:
```
auth   sufficient   pam_ldap.so
auth    required        pam_unix.so nullok_secure use_first_pass likeauth
```

---

### Post by jbronson on 2007-10-09
Thanks for the tip, elvis. That sorted out the double-password issue.

Anyone have any input on the second issue?  As of now, users are seen via LDAP when using 'getent passwd', but they cannot login.  I've created a 'host' keytab for the Ubuntu boxes, so they can get a TGT from the Kerberos controller.  Do they need a keytab with 'host' and 'ldap' services for users to login properly?

Thanks!

---

### Post by lokimon on 2007-10-16
> **jbronson said:**
> Thanks for the tip, elvis. That sorted out the double-password issue.

yes, i was seeing the same behavior and that fixed it.

> Anyone have any input on the second issue?  As of now, users are seen via LDAP when using 'getent passwd', but they cannot login.  I've created a 'host' keytab for the Ubuntu boxes, so they can get a TGT from the Kerberos controller.  Do they need a keytab with 'host' and 'ldap' services for users to login properly?

Thanks!

i am still unable to log in with LDAP users, although my local account works fine.

i'm not sure why this is as i was able to get this to work under red hat (which has LDAP client settings in their GUI network setup)

i'm not sure what the issue is, nor how to troubleshoot it.

my OpenLDAP server is an Xserve PPC running 10.4.8 (and Open Directory)

i have solaris (8+9) and macosx 10.4.8 clients connecting to it just fine, and as i said before i got a red hat client to authenticate to it just fine in the past.

the error i see in /var/log/syslog is:

pam_ldap: ldap_simple_bind Can't contact LDAP server

any ideas on where to go from here?

edit for more info:

my ubuntu box -> dell dimension 8200, ubuntu 7.04

---

### Post by elvis on 2007-10-17
Have you edited all of the /etc/pam.d/common-* files appropraitely?

---

### Post by blackjackchik on 2007-10-17
Hi. I need good howto too.

---

### Post by elvis on 2007-10-17
There's a quick and dirty guide on the Ubuntu community docs here:
[https://help.ubuntu.com/community/LDAPClientAuthentication?highlight=%28ldap%29](https://help.ubuntu.com/community/LDAPClientAuthentication?highlight=%28ldap%29)

---

### Post by lokimon on 2007-10-17
> **elvis said:**
> Have you edited all of the /etc/pam.d/common-* files appropraitely?

well, i edited them all, as i was told to do in the community docs, is there anything else you were thinking of?:

#
# /etc/pam.d/common-account - authorization settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authorization modules that define
# the central access policy for use on the system.  The default is to
# only deny service to users whose accounts are expired in /etc/shadow.
#
account sufficient      pam_ldap.so
account required        pam_unix.so

#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
auth    sufficient      pam_ldap.so
auth    required        pam_unix.so nullok_secure use_first_pass likeauth



#
# /etc/pam.d/common-password - password-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define  the services to be
#used to change user passwords.  The default is pam_unix

# The "nullok" option allows users to change an empty password, else
# empty passwords are treated as locked accounts.
#
# (Add `md5' after the module name to enable MD5 passwords)
#
# The "obscure" option replaces the old `OBSCURE_CHECKS_ENAB' option in
# login.defs. Also the "min" and "max" options enforce the length of the
# new password.
password   sufficient pam_ldap.so
password   required   pam_unix.so nullok obscure min=4 max=8 md5 use_first_pass

# Alternate strength checking for password. Note that this
# requires the libpam-cracklib package to be installed.
# You will need to comment out the password line above and
# uncomment the next two in order to use this.
# (Replaces the `OBSCURE_CHECKS_ENAB', `CRACKLIB_DICTPATH')
#
# password required       pam_cracklib.so retry=3 minlen=6 difok=3
# password required       pam_unix.so use_authtok nullok md5


#
# /etc/pam.d/common-session - session-related modules common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of modules that define tasks to be performed
# at the start and end of sessions of *any* kind (both interactive and
# non-interactive).  The default is pam_unix.
#
session sufficient      pam_ldap.so
session required        pam_unix.so
session optional        pam_foreground.so

---

### Post by ac3buddy on 2007-11-06
Hi good day. Im ace a student from philippines 
and ive been having problem regarding the installation and configuration of kerberos in feisty fawn. Is there any complete and definite guides in configuring kerberos, from extracting the tar files to final configurations . thanks so much

---

