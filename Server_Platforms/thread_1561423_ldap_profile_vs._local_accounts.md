---
title: "ldap profile vs. local accounts"
date: 2010-08-26
forum: Server Platforms
---

### Post by kuda on 2010-08-26
Hi,

I have this ldap profile on clients:

[open_ldap]
nss_passwd=passwd: compat ldap
nss_group=group: compat ldap
nss_shadow=shadow: compat ldap
pam_auth=auth       required     pam_env.so
 auth       sufficient   pam_unix.so likeauth nullok
 auth       sufficient   pam_ldap.so use_first_pass
 auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
 account    sufficient   pam_ldap.so
 account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow use_authtok
 password   sufficient   pam_ldap.so use_first_pass
 password   required     pam_deny.so
pam_session=session    required     pam_limits.so
 session    required     pam_mkhomedir.so skel=/etc/skel/ umask=0077
 session    required     pam_unix.so
 session    optional     pam_ldap.so

just wonder how to adjust this one to be able to log in (and add new local accounts) when clients are not on the same network segment as LDAP server.

Thanx in advance for all suggestions.k.[COLOR="Black"][/COLOR]

---

### Post by craigp84 on 2010-08-26
i can't understand your question

---

### Post by kuda on 2010-08-26
Ok, I am sorry i will try to descibe situation:
I have clients (Ubuntu 10.04) with ldap profile configured and people wish to take their machines home and work there. the problem is that i don't have any local account they can use, they have only ldap account which is impossible to use at home of course ... when i try to make new local account, i get only error .. it's because ldap profile is in use. question was only how to adjust this profile in order to be able to login at home for example ...

---

### Post by craigp84 on 2010-08-26
Ok cool. The most common solution to your problem is to cache login credentials on the local machines (laptops).

This means that first login must occur when connected to the network, however subsequent logins can be with / without the network (although you can set limits as to how long the laptop can be away from the network if you wish).

[https://help.ubuntu.com/community/PamCcredsHowto](https://help.ubuntu.com/community/PamCcredsHowto)

---

### Post by kuda on 2010-08-27
Ok, thnx for useful link, exactly what I need!k.

---

### Post by druhboruch on 2010-08-27
Unfortunately this how to is not up-to-date.

It didn't work for me.

If you get it to work in lucid, plese post your config files.

Edit:
The version of libpam-ccreds from Maverick is to be used.
There is a bug and discussion on Launchpad about it.

---

