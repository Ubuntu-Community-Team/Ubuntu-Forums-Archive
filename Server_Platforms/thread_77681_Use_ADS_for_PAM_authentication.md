---
title: "Use ADS for PAM authentication"
date: 2005-10-17
forum: Server Platforms
---

### Post by Faw on 2005-10-17
I have an Windows 2003 with Active Directory and an Ubuntu 5.10 server. What I want to do is do all the user authentication with the Windows server but I don't want to create accounts for users in the Ubuntu server. 

Right now I can authenticate users with the Windows server (kinit works) but I have no idea how to setup PAM to use it. I have searched for howtos but none of them give a simple explanation of how to do this (or one I'll understand).

The Ubuntu server will be a IMAP (Cyrus/Postfix) SAMBA server.

---

### Post by LordHunter317 on 2005-10-17
Read the Official Samba HOWTO (on samba.org) and look into setting up winbind, which sounds like it'll work for this application.

---

