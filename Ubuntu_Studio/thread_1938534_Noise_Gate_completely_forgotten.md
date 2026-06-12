---
title: "Noise Gate completely forgotten?"
date: 2012-03-09
forum: Ubuntu Studio
---

### Post by pepsifx357 on 2012-03-09
I need a free noise gate plugin.  Does one exist?  I've downloaded a few off of the internet that won't even install.

I'm at a loss, It's a simple plugin that most engineers use all the time for drums, yet they're hard to find.

Does anyone know where I can find one?

Thanks,

Ben

---

### Post by BcRich on 2012-03-10
Hi pepsifx357
I would recommend installing Autostatic's PPA, the software I've installed from it has been the most reliable across all my different versions of ubuntu. Sadly, it seems that Autostatic is not going to maintain his PPA any more :( and recommends another (which i have not tried yet). Nonetheless, if you are interested you can find instructions on installing the Autostatic PPA at [https://launchpad.net/~autostatic/+archive/ppa](https://launchpad.net/~autostatic/+archive/ppa) once the PPA is installed open synaptic (or whatever package manager you use) and install abgate (which is an LV2 noise gate plugin). 
I realise this might seem like overkill, but there are alot of other useful sound engineering plugins and software (that become available to you once the new PPA is installed) that you might find useful.

---

### Post by CivilizationII on 2012-03-10
> **pepsifx357 said:**
> I need a free noise gate plugin.  Does one exist?  I've downloaded a few off of the internet that won't even install.

I'm at a loss, It's a simple plugin that most engineers use all the time for drums, yet they're hard to find.

Does anyone know where I can find one?

Thanks,

Ben


Steve Harris plugins contains one gate, they are good and available under LADSPA plugins system (named swh-plugins under Ubuntu repo.) and LV2 plugins system (named swh-lv2 for Ubuntu 12.04; but i think you have to do a manual installation of the plugin over LV2 for Ubuntu 10.04, LV2 itself being inside Ubuntu repo).

---

