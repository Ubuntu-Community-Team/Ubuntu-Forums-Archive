---
title: "How do PAM and LDAP like each other?"
date: 2012-11-03
forum: Server Platforms
---

### Post by pawnrocket on 2012-11-03
Hi Everyone, 

I am doing a project for school. 

I have to design a password policy and implement it using Linux. 

I am using LDAP for the configuration of network accessible authentication. 

How do PAM and LDAP work together? If I make changes in /etc/login.defs but then configure OpenLDAP with a different setting which on wins? Or does using OpenLDAP make is so that the settings in /etc/login.defs are only processed for local users? 

Thanks in advance.

---

### Post by SeijiSensei on 2012-11-03
As far as I know, if pam_ldap is the default authentication module, then that is what will be tried first.  You need to look at the contents of /etc/pam.d, especially the common-auth and common-password files.  By default they use pam_unix which authenticates against /etc/passwd and /etc/shadow.

---

### Post by pawnrocket on 2012-11-03
Thanks, I'll look into that.

---

### Post by sandyd on 2012-11-03
Generally, it works something like this

PAM functionality is defined by modules ( *.so libraries) that are loaded. LDAP functionality is provided through pam_ldap.so.

When the user logs in, or does anything that requires pam, the system looks up the corresponding PAM file (there are ones for login, proftpd, pureftpd, .etc .etc), and auths using the libraries listed there. If you have the LDAP library loaded, it either looks into pam_ldap.conf (this is for **fedora**, the settings are placed elsewhere in other distros) for the information used to access the LDAP server (i.e. bind password, address) or in some configurations, this is done through the nslcd backend (/etc/nslcd.conf) instead. The nslcd method uses libpam-ldapd (the same backend as NSS (libnss-ldapd)), while the older method uses libpam-ldap.

This explanation is a bit simplified (no explanation of the auth required/ account required, .etc .etc), but it should suffice

---

