---
title: "Likewise-open woes"
date: 2009-03-23
forum: Server Platforms
---

### Post by dkinfl on 2009-03-23
Made the switch to Ubuntu linux.  Things are going great, but I can not join my machine to the domain.  I have likewise-open version 4 installed on Ubuntu 8.10.  I enter the command and get the following:

sudo domainjoin-cli join XXXX.local Administrator
Joining to AD Domain:  XXXX.local
With Computer DNS Name name.XXXX.local

[email]Administrator@XXXX.local[/email]'s password: *************

20090323150048:WARNING:Short domain name not specified. Defaulting to 'XXXX'
Error: Unable to join domain [code 0x0008000e]
Domain join operation failed to create the computer account in Active Directory. Common causes are a bad
administrator password, a bad OU name, or an existing computer account without modification permissions.
20090323150053:ERROR:Unable to join domain [CENTERROR_DOMAINJOIN_JOIN_FAILED]
Domain join operation failed to create the computer account in Active Directory. Common causes are a bad administrator password, a bad OU name, or an existing computer account without modification permissions.
-------------------------------------
Now I cant figure out why it is trying to shorten the domain name.  I am the AD and DNS admin at my company, and I can assure you nothing will answer to the request for a domain named XXXX, only for XXXX.local.  Any ideas as to why this is occuring?

---

### Post by nunhead_man on 2009-07-14
I'm having exactly this problem  - have you now solved it?  

Wondering what runs your domain  - is it Windows 2003 server?

And if so whether a recent service patch has broken something?

Best to all

---

### Post by cariboo on 2009-07-14
Moved to server platforms, as some the Likewise people monitor this forum.

---

### Post by HermanAB on 2009-07-14
This may help:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

---

