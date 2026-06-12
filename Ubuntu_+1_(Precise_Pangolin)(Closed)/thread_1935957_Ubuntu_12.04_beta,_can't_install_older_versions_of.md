---
title: "Ubuntu 12.04 beta, can't install older versions of wine."
date: 2012-03-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jgcsd on 2012-03-05
Yes, I know it's a beta so things may just be broken. But I thought I'd ask just in case somebody can help.

I usually use 10.04, and I play a game using WINE that works fine. I thought I'd try it on 12.04, but a patch won't install. WINE errors saying "Internal errors - Invalid parameters received". 

Since I installed it on 10.04 ages ago when WINE was around patch 1.3 or maybe lower, I thought I'd try an older version of WINE in 12.04, instead of 1.4 rc6 which is what is installed.

WINE 1.4, 1.3 and 1.2 all appear in the synaptic package list, but all these versions install WINE 1.4 rc 6 and not older versions of WINE. Or at least they seem to.

Does anyone know what's going on, how I can install older versions of WINE in 12.04, or maybe how to fix the error I had?

---

### Post by nothingspecial on 2012-03-05
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by grahammechanical on 2012-03-05
I have been using 12.04 since before it was alpha 1. I upgraded from an 11.10 install. So, there were still many 11.10 components on the system.

I use wine 1.4 installed from a PPA but the version in the Software Centre was 1.3 and so during an update I got updates to both 1.3 and 1.4. I somehow got both installed but the wine that activates is 1.4

Now that the Software Centre has been upgrade to the 12.04 version it is offering wine 1.4.

If you install Synaptic Package Manager (not installed by default in 11.10 or 12.04) and search for wine you will find that it has a wine 1.2 that you can install.

Most probably you will need to un-install those later versions of wine otherwise the latest version will be the one activated when you try to load the program.

Regards.

---

### Post by dino99 on 2012-03-05
you might found what is wrong on your wine installation: mainly its better to start with a new .wine (rename or delete the previous one) as 1.4 is the most bug free release but lot of settings/dependencies have been modified recently. So trying to install an older wine release is not the way to go.

---

### Post by mc4man on 2012-03-05
All you're going to find in 12.04 as far as pre-built packages is the 1.4+ version, the 1.2, 1.3 are just transitional packages. (basically empty

---

