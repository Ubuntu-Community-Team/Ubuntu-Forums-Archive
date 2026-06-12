---
title: "adduser not working with nis"
date: 2012-01-18
forum: Server Platforms
---

### Post by dshrek on 2012-01-18
I have installed NIS on our servers (Ubuntu Server 10.04). Everything is working fine, except for one thing.

I added "nis" in /etc/pam.d/common-password:
password        [success=1 default=ignore]      pam_unix.so obscure sha512 nis

Users can now change their passwords on any machine using passwd in the usual way. This works fine. 
The problem arises if I try to change passwords for root or for a user as root. passwd asks for "NIS server root password:", but at that point I have to enter the root or the users(!) password, depending on which password I try to change. So I am not able to change passwords as root if I don't know the users password. 
In addition, if I try to add a user with adduser, it is not possible to set the users password at all. At the stage where passwd is executed an entry for the new user in /etc/shadow exists, but is disabled with a "!" in the password hash field. It seems that nothing works for "NIS server root password:". I have tried the root password and simply "enter".

---

