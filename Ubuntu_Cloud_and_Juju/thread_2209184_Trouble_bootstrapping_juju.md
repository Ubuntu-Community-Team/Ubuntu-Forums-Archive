---
title: "Trouble bootstrapping juju"
date: 2014-03-04
forum: Ubuntu Cloud and Juju
---

### Post by xander3 on 2014-03-04
Hi all,

I am investigating MAAS with juju on Ubuntu 12.04.4LTS. (also tried 13.10...)

I have set up my server(s) using various tutorials, but I keep getting 403 errors when bootstrapping juju.

I have tried it as root and as the local administrator. Everytime I keep getting "[FONT=courier new]2014-03-04 15:20:50 ERROR juju supercommand.go:282 cannot start bootstrap instance: gomaasapi: got error back from server: 403 FORBIDDEN[/FONT]" errors.

 Is there anyone who can give me a clue, so I can continue my installation.

Setup information:
Ubuntu 12.04.4
MAAS 1.4+bzr1693+dfsg-0ubuntu2.2~ctools0
juju 1.16.6

[COLOR=#333333][FONT=UbuntuRegular][SOLUTION (at least for me)] I am using plain PCs to test the setup. Therefore I am forced to use WOL instead of e.g. IPMI/iDRAC etc. It seems that when you configure the node as using WOL, you have (!!) to enter the MAC address explicitly.[/FONT][/COLOR]

---

