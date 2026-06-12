---
title: "Primary Group SID is inconsistent?"
date: 2009-08-30
forum: Server Platforms
---

### Post by wbluo on 2009-08-30
Hi everyone,

I installed a Ubuntu 8.04.3 LTS with OpenLDAP 2.4.9 and Samba 3.0.28a to authenticate both Windows XP users and Ubuntu desktop users. However, I cannot login to my Windows XP desktop PCs via authentication through the aforementioned ubuntu server. I observed the following on the server.

When I typed "net groupmap list" on the server, I had the following:

Domain Users (S-1-5-21-4094830598-1919084798-598250124-513) -> Domain Users

After I created a user account "peter" with primary group "Domain Users" using "smbldap-useradd", I typed "pdbedit -v -L" on the server, and observed the following:

User SID:                 S-1-5-21-4094830598-1919084798-598250124-61064
Primary Group SID:  S-1-5-21-217487775-1352538329-3199194353-513

It seems that the Primary Group SID is different from what I saw using "net groupmap list". Why? I am confused. I think that might be the reason why the server cannot authenticate users from Windows XP PCs. Any help or suggestions will be highly appreciated.

Peter

---

### Post by capscrew on 2009-08-30
Try looking at MS [[COLOR="DarkSlateGray"]_**Services For Unix**_[/COLOR]]("http://en.wikipedia.org/wiki/Microsoft_Windows_Services_for_UNIX") (SFU).  The current version is 3.5

---

### Post by wbluo on 2009-08-31
Thanks for sharing this. But I'd like to fix the aforementioned problems on my server. Do you have any suggestions?

---

