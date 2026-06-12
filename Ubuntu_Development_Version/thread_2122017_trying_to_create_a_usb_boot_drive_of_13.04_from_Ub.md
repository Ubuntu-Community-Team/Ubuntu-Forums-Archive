---
title: "trying to create a usb boot drive of 13.04 from Ubuntu"
date: 2013-03-03
forum: Ubuntu Development Version
---

### Post by Tommy The Cat on 2013-03-03
Ok, so here's my problem. I've got an .iso of Ubuntu Studio 13.04 that I'm trying to put on a USB stick and Ubuntu's startup disk creator keeps creating folders in the /tmp directory and then giving me errors complaing that it can't read from those directories. I don't know how to chmod the problem away given that these folders come up using randomly generated names during the installation process. But this is about all I know. What can I do from here? I did create a stick from the regular version of Ubuntu 13.04 that seemed to work just fine, but I want to move to 13.04 studio.

Edit: I should probably mention that I'm currently running 12.10 64-bit.

---

### Post by ventrical on 2013-03-03
Try 'discarded on shutdown unless you save them elsewhere'.

 I don't know why but for quite some time there have been ssome bugs with development releases (and even stable) and this option seems the only option to work in some cases.

---

### Post by Tommy The Cat on 2013-03-03
Worked like a charm. I'm now in Ubuntu Studio 13.04 as we speak. Not sure I like it, but that's beside the point. Thanks so much.

---

### Post by ventrical on 2013-03-04
Your welcome.

This problem started in development release 11.10 , Oneric Ocelot and persisted right on through all of the releases. In the interim between then and now other distros and installs (including Lucid Lynx) have begun to fail with reference to SDC. I currently use the MM Maveric Meekat 10.10 which is rather stable.

It has been discussed and reported on launchpad but this bug is persistent right on through. It is also rather carpicious .. it will come and go and come again.. so there may even be a security problem here. It is a major regression. However, it will often work with the 'discard on shutdown' option .. so this may be a clue as to what the bug is.

---

