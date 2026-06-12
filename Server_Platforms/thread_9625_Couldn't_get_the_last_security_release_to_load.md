---
title: "Couldn't get the last security release to load"
date: 2004-12-30
forum: Server Platforms
---

### Post by bob k on 2004-12-30
I did an apt-get update
apt-get upgrade

The update found the two modules to upgrade, although small, the apt-get upgrade held them back and did not do the upgrade

---

### Post by Juergen on 2004-12-30
Since it depends on what is installed, you probably should tell exactly what packages are held back. 
I'm using Synaptic, but doesn't apt tell you why it doesn't want to install them?
Maybe you have to do a dist-upgrade

I just updated successfully:
imlib-base
imlib1
gdk-imlib1

---

