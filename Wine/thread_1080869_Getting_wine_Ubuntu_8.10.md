---
title: "Getting wine Ubuntu 8.10"
date: 2009-02-25
forum: Wine
---

### Post by invincibletoviruses on 2009-02-25
Can someone give me step by step instructions 4 installing wine(stable version) on ubuntu 8.10.And how to enable it.(newbe).thanks

---

### Post by whoop on 2009-02-25
Run synaptic, search for wine, right click mark for installation. Click apply. done.

---

### Post by invincibletoviruses on 2009-02-25
synaptic gives 4 options:wine,wine-dev,wine-gecko,winefish:i chose wine.Then it says mark additional required changes? when i click mark 
the synaptic says its going to install wine-gecko also. Do i continue ?(press apply)

---

### Post by sgosnell on 2009-02-25
Yes.  There are some dependencies.  The only time to worry is when it wants to remove a long list of apps.  Just go ahead and install it, and it should show up in the menu under Applications.  Configure it as necessary, and there is nothing else to do.  To install Windows .exe programs, just run them, and wine will take over and do the install automagically.  Then you just run the Windows program from the desktop icon or from the file manager.  Wine does everything in the background.

---

### Post by invincibletoviruses on 2009-02-25
thanks!

-Rubin

---

### Post by invincibletoviruses on 2009-02-25
one more question does wine pose any security threat to my computer?

---

### Post by kidux on 2009-02-25
Go to [www.winehq.org](www.winehq.org) and read the docs there. Also look at the app db as well to find out tips and tricks for the software you are trying to install. Plus they have a more current stable version on their site than is in the repositories.

---

### Post by invincibletoviruses on 2009-02-25
couldn't find much about the security of wine but did find the app db useful!

---

### Post by kidux on 2009-02-25
> **invincibletoviruses said:**
> couldn't find much about the security of wine but did find the app db useful!
It's not the security of WINE you need to be concerned with, but rather the security of the SOFTWARE run it since it is Windows based and going to have the same vulnerabilities. One thing to remember is to not do anything as root (or sudo, in Ubuntu's case) that has to do with WINE. You do not want WINE to have any kind of escalated privileges.

---

### Post by invincibletoviruses on 2009-02-25
thanks for all your knowledge!

-Rubin

---

### Post by kidux on 2009-02-25
No prob man! Have fun!

---

