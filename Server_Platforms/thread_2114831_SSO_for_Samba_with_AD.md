---
title: "SSO for Samba with AD"
date: 2013-02-11
forum: Server Platforms
---

### Post by karl meier on 2013-02-11
Hello,

I have a problem and can't find a solution. I searched for days now and nothing seem to work.

I have a Linux server and a Windows domain. 
I try to share documents with samba and the user should be able to get to this samba share without typing the passwort again.

I need a single sign on for samba shares.

I put the server into the domain with likewise-open and I'm able to log me in with my AD-Account.


What I have to do now. I tried adding "winbind use default domain" to my smb.conf but it didn't work.

Any tips or guides for me? 


Ubuntu 12.04.1 LTS
Samba 3.6.2
Windows 2008 domain

---

