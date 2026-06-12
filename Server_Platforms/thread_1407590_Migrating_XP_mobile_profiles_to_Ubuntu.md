---
title: "Migrating XP mobile profiles to Ubuntu"
date: 2010-02-15
forum: Server Platforms
---

### Post by thabeat on 2010-02-15
I’ve voluteered on a NGO to work on a migration project to Open Software. 



  Actually there are something like 25 workers on XP machines with AD on a Samba domain with tdbsamba database. 



  Because of the workers, we decided to migrate on Ubuntu 9.04. 
  I started working on drivers for special hardware and stuff, because I thought it would be pretty easy to join a SAMBA/LDAP PDC. 4 days ago the actual guy on IT told me there wasn’t any LDAP… 



  And I have no clue how to login a Ubuntu 9.04 to this domain.
I’m not very good at this, and my first thought was to make the server work with LDAP, but obviously they would rather migrate step by step (I still have the problem with the designers department and Photoshop). And do not like the idea to change the server for now, for the moment is just a viability project, and they would like to see it working before changing anything.


I've tried likewise-open, which actually doesn't work witg NT4-like systems only ADs, and also with plain winbind, but it seems all the manuals and HOWTO's I can find are a little bit outdated or are using a KERBEROS server, which I don't have, and then I'm missing something.


I mounted a VM with a WinXP, on it I just say the WinXP to login against MEGOSG (the Domain name) and bind it with root and password on the Samba server (192.168.1.10). Then I'm able to login as any profiled user.


How can I do something like that on Ubuntu? Just as a client, I mean...

---

