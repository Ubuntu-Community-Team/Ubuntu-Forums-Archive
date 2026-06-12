---
title: "LDAP Lookup partially working"
date: 2007-11-09
forum: Server Platforms
---

### Post by steenbras on 2007-11-09
I apologise if this is a FAQ - I have spent ages searching for answers and have not yet had any luck.

I have 2 Gutsy installations (running on VMWARE). One is acting as an LDAP server. I have 2 users defined in the LDAP directory.

The other Gutsy server is an LDAP client. I want to be able to log on to the LDAP client through SSH and for the authentication to come from LDAP. The problem is that it appears that LDAP is only looked at if the user already exists in the local /etc/passwd file. I can change the password in LDAP for that user and the new password is successfully checked (as is the local password).

However the other user, who is NOT in /etc/passwd, cannot be found. A getent for that user returns nothing, and they can't log in.

I can't for the life of me figure out why this is. My configuration is as below (all commented lines removed for brevity):

/etc/nsswitch.conf
-----------------------
[FONT="Courier New"]passwd:         files ldap
group:          files ldap
shadow:         files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
[/FONT]

/etc/ldap.conf
-----------------
[FONT="Courier New"]host server.example.com
base dc=example,dc=com
ldap_version 3
rootbinddn cn=admin,dc=example,dc=com
pam_password md5
[/FONT]

(actual server dns names replaced above)

/etc/pam.d/common-auth
-------------------------------
[FONT="Courier New"]auth    sufficient      pam_ldap.so nullok_secure
auth    required        pam_unix.so use_first_pass
[/FONT]

/etc/pam.d/common-account
-----------------------------------
[FONT="Courier New"]account sufficient      pam_ldap.so
account required        pam_unix.so
[/FONT]

/etc/pam.d/common-password
-------------------------------------
[FONT="Courier New"]password   sufficient pam_ldap.so
password   required   pam_unix.so try_first_pass nullok obscure md5
[/FONT]

/etc/pam.d/common-session
----------------------------------
[FONT="Courier New"]session sufficient      pam_ldap.so
session required        pam_unix.so
session optional        pam_foreground.so
[/FONT]

If I've left off any config files here, please let me know. I'm sure I've done something stupid - any help greatly appreciated.

Thanks

---

### Post by steenbras on 2007-11-09
SOLVED - actually not much documentation around this, so hopefully my findings can help someone else.

It seems that in order for host authentication to work with LDAP, your LDAP entry MUST contain an objectClass definition for posixAccount, and the mandatory attributes associated with that objectClass.

I think that what was happening in my case is that the account lookup was failiing on LDAP, because of this missing attribute, but for my id was falling back to files, then the authentication was succeeding on LDAP. However in the case of the other user, the account lookup fails in LDAP, there was no local definition in files, so the connection just failed.

---

