---
title: "Samba Share Printer Problem"
date: 2013-02-23
forum: Server Platforms
---

### Post by sayedahmad on 2013-02-23
I have installed canon ImageRunner 1133 in cups print server on   ubntue server 12.04 and shared it through samba server for windows 7 clients it works fine.

The problem is that I want every user to be prompted for username and password when they click the shared printer but I am unable to do this in samba even I set " guest ok = no" under printers in samba but still it is not asking for username/password prompt.

Note: When I share a directory from samba server for windows 7 clients it prompts for username and password but printer does not 



please help if you have any idea.

---

### Post by chrisguk on 2013-02-23
> **sayedahmad said:**
> I have installed canon ImageRunner 1133 in cups print server on   ubntue server 12.04 and shared it through samba server for windows 7 clients it works fine.

The problem is that I want every user to be prompted for username and password when they click the shared printer but I am unable to do this in samba even I set " guest ok = no" under printers in samba but still it is not asking for username/password prompt.

Note: When I share a directory from samba server for windows 7 clients it prompts for username and password but printer does not 



please help if you have any idea.

Have you setup "Security = user"

Also I normally setup a separate file called smbusers to store the users in but you dont have to do this really.  Are you on a large network? is that why you need to password protect the printer or is this just a lab test?

---

### Post by sayedahmad on 2013-02-23
I have already set "user = security"
yes I am on a large network

---

