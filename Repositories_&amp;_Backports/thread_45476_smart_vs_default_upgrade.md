---
title: "smart vs default upgrade"
date: 2005-06-30
forum: Repositories &amp; Backports
---

### Post by akcanadianeh on 2005-06-30
Ok, I don't know how n00b this may sound, but what is the practical difference between a default and a smart upgrade in Synaptic, why would I use each, and which one does the Ubuntu Update Manager use?

---

### Post by Devi0s on 2005-06-30
*From the Synaptic Help menu:*

**Default Upgrade**

The default upgrade method marks upgrades of installed packages only. If the later version of a package depends on not installed packages or conflicts with an already installed package, the upgrade will not be marked.

[B]Smart Upgrade (Dist-Upgrade)

[/B]The smart upgrade method tries to resolve package conflicts intelligently. This includes installing additional required packages and preferring packages with higher priority.

Smart upgrade is also known as dist-upgrade in the console tool apt-get.

---

### Post by akcanadianeh on 2005-06-30
Thanks for the reply, Devi0s. I read that in the help file too. What I haven't been able to find out is this: Is there a downside to always using the smart update, and does the Ubuntu Update Manager do a default or a smart?

---

### Post by Segovia on 2005-06-30
[QUOTE=akcanadianeh]Ubuntu Update Manager do a default or a smart?[/QUOTE]
I'm fairly certain that Ubuntu Update Manager does a default upgrade.  The reason I say that is because on one occasion, it informed me that I should launch Synaptic and do a Smart Upgrade for certain packages.

If you're only using the official Ubuntu repositories and Hoary/Warty, you can simply do a dist-upgrade (smart) every time (or just follow the advise of Ubuntu Update Manager) - since only security patches will be on those repos.

If, on the other hand, you're using some third-party repositories, then you should always take care not to do *either* type of upgrade blindly.

---

