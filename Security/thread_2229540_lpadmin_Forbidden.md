---
title: "lpadmin Forbidden"
date: 2014-06-13
forum: Security
---

### Post by gallay-charles on 2014-06-13
Hi everyone,

I am currently trying to use lpadmin with a normal user. Unfortunately I am getter an Error lpadmin: Forbidden I don't understand how it is possible. In fact I check /usr/sbin and the programme lpadmin is own by root and others can execute it (-rwxr-xr-x 1 root    root       22528 Apr 10 20:40 lpadmin). So if I understand correctly the setuid concept, I should be running with some temporary root permission. But I don't understand why this error occur.

I know that simply adding the user in the adm group resolve the problem. But I don't want to do that, does anyone have a solution?

I know that I can add the user in the lpadmin group but I am trying to find a way that might work on Mac OSX because the printServer I am using is running Mac OSX :/

Otherwise If someone known exactly why when printing to an smb printer my job's names are "remote download document"??? 

Thanks for your help,

Charles

---

