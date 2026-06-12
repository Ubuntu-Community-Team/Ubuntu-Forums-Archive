---
title: "Samba ADS"
date: 2010-05-05
forum: Server Platforms
---

### Post by aethiolasa on 2010-05-05
I'm attempting to connect samba to an active directory setup however when running the command 'net ads join -U <myusername>' I run into an issue.  The way our domain is configured I want to join one domain lets called it sub.example.local but my account(the one that has rights to add to testsub.local) is actually from example.local.  So when I do something like 'net ads join -U aethiolas' it interprets that as 'net ads join -U [email]aethiolas@sub.example.local[/email]' however if I try to run 'net ads join -U [email]aethiolas@example.local[/email]' it will interpret it is as 'net ads join -U [email]aethiolas@example.local@sub.example.local[/email]'.  Obviously neither of these work!  Any help would be GREATLY appreciated b/c unfortunately I don't control the domains so I can't change my account...

---

