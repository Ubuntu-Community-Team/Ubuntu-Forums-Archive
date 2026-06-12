---
title: "Updating VMWare Workstation from 6.5.1 to 6.5.2 doesn't seem to work"
date: 2009-07-19
forum: Virtualisation
---

### Post by liquidcross on 2009-07-19
I've been running VMWare Workstation 6.5.1, and recently downloaded the update for 6.5.2. I converted the .rpm to a .deb using alien, then installed it normally. The install was successful, but when booting VMWare, it still claims it's 6.5.1, and tells me to download the update! Even in Synaptic, it's listed as 6.5.2. Did I miss something?

---

### Post by TJet1.8 on 2009-07-19
Well...although coverting rpm's to .deb work "in theory", I woouldn't have gone that way. You never know for sure if alien does the conversion correctly.
Remember that rpm's are geared more towards RedHat distro's.

I found that dounloading/using the VMware .bundle package works better on Ubuntu.
I would try re-installing the .bundle version.

BUT, before you do that...did you recompile the modules?
Do the following first before re-installing:

sudo apt-get install build-essential linux-headers-$(uname -r)
sudo /usr/bin/vmware-modconfig --console --install-all

See if that works.

Good luck.

---

### Post by liquidcross on 2009-07-19
That did it. Thanks!

---

### Post by TJet1.8 on 2009-07-19
No problem....I'm glad your up and running :)

---

