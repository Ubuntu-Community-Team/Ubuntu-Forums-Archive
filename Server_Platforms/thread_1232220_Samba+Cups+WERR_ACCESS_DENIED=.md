---
title: "Samba+Cups+WERR_ACCESS_DENIED="
date: 2009-08-05
forum: Server Platforms
---

### Post by mcarrara on 2009-08-05
it equals four days of pulling out what little hair I have.

Situation:
Ubuntu 8.04LTS with CUPS and SAMBA from APT-GET
did dist-upgrade so I should be up to date with all packages.
Running on VMWare ESXi if that makes any difference.

Used Cups web interface to install HP laser printer.  I can print a test page from the interface.  I assume cups is working correctly.

Samba is configured to use winbind.  I created a share and am able to access it from a Windows client correctly, so it APPEARS that samba is working correctly.

Now to combine the two.  I am using the latest windows PS drivers from cups.org and the procedure in the official Samba How To.  I modified the how to to reflect the new file names. The cupsdaddsmb script gives me the dreaded WERR_ACCESS_DENIED error, so I checked everything I read about on the net:
1. use client driver = no
2. print admin = techguy
3. admin users = techguy
4. run as root (sudo su)
5. file and directory privileges all 0777
6. used rpcclient to grant techguy SePrintOperatorPrivilege

Ran the steps manually and everything works until I try to setdriver then I get the WERR_ACCESS_DENIED error.

I even started with a completely fresh install of Ubuntu with the same results.

There must be some small step I am missing.  Any ideas???

---

### Post by mcarrara on 2009-08-05
I knew it was something simple.

Today while trying and retrying I used root, techguy(my 'fake' root account) me, me as a domain user nothing worked UNTIL I put quotes around me as a domain user like:
"DOMAIN\me"  That worked and I have actually printed a page.  Now if I can get my Samba PDC to work . . .

Mark

---

