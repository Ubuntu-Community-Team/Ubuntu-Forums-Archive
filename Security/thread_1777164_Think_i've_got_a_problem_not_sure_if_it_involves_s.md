---
title: "Think i've got a problem not sure if it involves security at the moment ?"
date: 2011-06-07
forum: Security
---

### Post by Mat11 on 2011-06-07
Hi i used the Teriminal and input sudo apt-get update and apt-get upgrade and pressed the Y feeling tired.

All i saw was 1 to upgrade which i clicked Y.

I ended up with the Adobe flash-plugin. So i went to uninstall it because i already have Gnome Gnash player which is perfectly good.

I ran the command sudo apt-get remove and got the output:

sudo apt-get remove adobe-flashplugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'adobe-flashplugin' can't be removed
The following package was automatically installed and is no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When i ran the command autoremove i just get reference to nspluginwrapper what is happening ?

Hope someone can help ?

Matt

---

### Post by Hopping_Ubu on 2011-06-07
> **Mat11 said:**
> Hi i used the Teriminal and input sudo apt-get update and apt-get upgrade and pressed the Y feeling tired.

All i saw was 1 to upgrade which i clicked Y.

I ended up with the Adobe flash-plugin. So i went to uninstall it because i already have Gnome Gnash player which is perfectly good.

I ran the command sudo apt-get remove and got the output:

sudo apt-get remove adobe-flashplugin

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'adobe-flashplugin' can't be removed
The following package was automatically installed and is no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When i ran the command autoremove i just get reference to nspluginwrapper what is happening ?

Hope someone can help ?

Matt

Matt,

Have you tried using the Synaptic Package Manager? If you haven't I suggest you give it a try. Do a search for adobe-flashplugin. If you find it and the box is filled, then it is installed. To uninstall, click on the box, it will ask you if you want to reinstall, uninstall or uninstall completely. Chose uninstall completely and then select apply on the toolbar.  It will have you confirm if this is what you want to do and let you know what it is going to uninstall. Once you confirm that is what you want, click apply. It will return a box that says changes applied.

Hope this helps.   :)

Hopping Ubu

---

