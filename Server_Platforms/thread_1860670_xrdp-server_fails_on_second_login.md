---
title: "xrdp-server fails on second login"
date: 2011-10-15
forum: Server Platforms
---

### Post by stn21 on 2011-10-15
Hi,

on ubuntu-server (11.04 and 11.10) xrdp does not work correctly.

It can be installed as usual with 'apt-get install xrdp'. Then  login is possible from another computer.

But if you end the session (by closing) the client, then it is not possible to log in again. After entering the password nothing further happens, the session just hangs.

With ubuntu desktop-edition everything works fine.

Any hints on how I can get xrdp to run on ubuntu-server ?

THX, stn

---

### Post by anon0 on 2011-12-19
I can't get xrdp to work on Ubuntu Server 11.10

---

### Post by BertN45 on 2011-12-21
I had the same problem in the past. It is related to the authorization. xrdp also seems to process the "optional" authorization lines in the common-auth file in /etc/pam.d

One of those is samba. I solved the problem in the past my moving the samba authorization statement from /etc/pam.d/common-auth to the /etc/pam.d/samba itself directly after the include of common-auth.

---

### Post by buffchick on 2012-03-14
sorry to necro but considering it's only be a couple of months... did you resolve this? I'm having the same problem.

---

