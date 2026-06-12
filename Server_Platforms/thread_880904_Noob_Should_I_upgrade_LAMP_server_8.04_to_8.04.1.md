---
title: "Noob? Should I upgrade LAMP server 8.04 to 8.04.1?"
date: 2008-08-05
forum: Server Platforms
---

### Post by trans_lux on 2008-08-05
Sorry for this very basic question but wanted to know if upgrading a 8.04 LAMP server to 8.04.1 is a good idea or are there downsides? 

These would be the commands I would use:

Install update-manager-core if it is not already installed:

sudo apt-get install update-manager-core

Launch the upgrade tool:

sudo do-release-upgrade

Follow the on-screen instructions. 

Thoughts comments?

---

### Post by StickyStyle on 2008-08-05
8.04.1 is not a 'new release' per se, it's a roll-up of all the updates since 8.04 was released packaged into a single installer.  It's to save new users that say just downloaded 8.04 to not have to grab 4 months of updates right after an install.  If you do your 'apt-get upgrade' regularly, your are on *8.04.1*.


Think of it as Windows XP with SP3 built in on one disk (shudder).

---

### Post by trans_lux on 2008-08-05
Sticky thanks so much for the prompt reply. I'm so gun shy of running any updates/upgrades from all my Windows disasters. So I will run a quick apt-get upgrade.

---

