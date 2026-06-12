---
title: "[SOLVED] Updates to ubuntu"
date: 2008-01-15
forum: Server Platforms
---

### Post by maustin2 on 2008-01-15
I currently have a ubuntu 6.06.1 LAMP server with kernel 2.6.15-29-686smp. It is on a Dell PowerEdge SC430 tower.

I would like to stop getting KDE updates. Is there away to stop these update. I have searched, but found no answer. You guys are my last hope. I am willing to attempt a programming solution if that is the only way. But I would need a starting point.

---

### Post by foxylad on 2008-01-15
Apt-get will only update packages that are installed, so it sounds like you have KDE installed. Use apt-get to remove it, and the updates will stop.

---

### Post by Maxtorm on 2008-01-15
If you want to keep KDE, but just stop the updates, use the Force Version command in the Synaptic Package Manager. There is also likely a way to do this from the command line using one of the apt tools. You can use ```
dselect
``` to manipulate packages and under the Install menu you can use H to hold a package, but I'm not sure if this is analgous to Force Version.

---

