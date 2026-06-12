---
title: "A question about Kerberos"
date: 2009-12-09
forum: Security
---

### Post by tenmoi on 2009-12-09
Hi all,

I have set up a 389 DS and a KDC-MIT V. Users created on the DS can log on from any client machines on the LAN controlled by the DS.

I still wonder if the client - DS connection is secure? 
And this is my reasoning which I would appreciate any corrections if I am wrong:

1. pam_krb5 only contacts the KDC for authentication. If this succeeds then 

2. pam_krb5 calls pam_mkhomedir to prepare everything for a new session (I do not know if I am correct when I say "pam_krb5 calls pam_mkhomedir because I put this line in the /etc/pam.d/login file:
.....
session required pam_krb5 mkhomedir ../skel umask 002
)

3. At this point pam_krb5 needs such information as uid,gid, home directory, login shell, etc, so ... I GET LOST HERE. Is pam_krb5 going to contact the KDC and tells it to get the info from the DS or is it going to ask some program that owns the nsswitch.conf file to pull that info from the DS for it? If this were true then this connection would be unsecure if the DS is set up to allow all forms of binding.

THank you.

---

### Post by box2 on 2009-12-17
pam_mkhomedir is indeed great, but without specific information to feed it (like UID / GID / path to the new home directory / default shell / timezone of the user / etc etc) it just won't have that information.  This is where ldap can come in to save the day.  Add your user there, tell pam to find all user information like this from your ldap server and pam_mkhomedir will fill everything out without the need for making a local copy of the users information on every server in the posix account files (/etc/passwd, /etc/group, yattayatta).

good luck.

---

