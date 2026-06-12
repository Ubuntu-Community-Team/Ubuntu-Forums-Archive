---
title: "Win7 SP1 causing issues with Samba domain controller"
date: 2014-04-16
forum: Windows
---

### Post by bruto2 on 2014-04-16
I have recently been handed a small network of 9 win7 machines and a single Ubuntu server running as domain controller. Server is Ubuntu 10.04.4, current samba version is 3.4.7 using an LDAP back end, from my research all pretty standard setup.

This setup has worked great for 4 years without any issues with the exception of any client machine that is updated to SP1 will not load a user profile from the server. The accounts authenticate no problem, but throws the following error when trying to copy the user profile from the server:

```
Windows cannot copy file \\?\UNC\orb$NOCSC$\\USERNAME\profile.V2\ to location \\?\C:\Users\USERNAME.DOMAINNAME\. This error may be caused by network problems or insufficient security rights. 

Event ID 1509

```

This is the only error I have found so far and it does not present on any client without SP1. I have found a few suggestions online in regards to path length but I am unsure if that would be my specific issue given it has only shown up with SP1 clients. Only other changes to the Windows clients were the suggested changes on the Samba wiki [here]("https://wiki.samba.org/index.php/Registry_changes_for_NT4-style_domains").

Has anyone had similar issues? Did anyone else need to make other registry changes to get clients to talk with the server again? Have I simply made a ballsup or overlooked something painfully obvious?

Any help would be appreciated.

---

