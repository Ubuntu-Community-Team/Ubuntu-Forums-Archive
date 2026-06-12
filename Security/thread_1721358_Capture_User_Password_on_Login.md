---
title: "Capture User Password on Login"
date: 2011-04-04
forum: Security
---

### Post by djbushido on 2011-04-04
So first off, this is not about hacking.
Second off, I'm trying to capture a user password on login (through gdm) such that I can re-use it for a service like Kerberos or AFS. The idea is that the user has to log in only once, and then I renew the tickets and tokens until they log out again. If there's a better way to do this, please let me know. In the mean time, any help is appreciated.

---

### Post by HermanAB on 2011-04-04
Howdy,

The correct way is to use PAM, the Pluggable Authentication Modules.

---

### Post by djbushido on 2011-04-04
Eh...

(From Wikipedia)

Despite PAM being part of the X/Open Single Sign-on (XSSO) standard, PAM on its own cannot implement Kerberos, the most common type of SSO used in Unix environments.

Due to limits of the PAM API, it is not possible for a pam module to request a Kerberos service ticket from a Kerberos Key Distribution Center (KDC), allowing the user to utilize the application without re-authenticating. pam_krb5 only fetches ticket granting tickets, which involves prompting the user for credentials and are only used for initial login in an SSO environment. To fetch a service ticket for a particular application, and not prompt the user to enter credentials again, that application must be specifically coded to support Kerberos, as pam_krb5 cannot itself get service tickets, although there are versions of PAM-KRB5 that are attempting to work around the issue.[2]

---

### Post by bodhi.zazen on 2011-04-04
From what you posted, I would suggest LDAP.

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

[https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html](https://help.ubuntu.com/10.04/serverguide/C/kerberos-ldap.html)

---

### Post by djbushido on 2011-04-04
Unfortunately I found out I am unable to install LDAP (working in a production environment, not my own, and under RHEL 5.4). Is there a way to actually capture the user password on login? Or am I just going to have to re-prompt?

---

