---
title: "Anyone know what the story is with fingerprint scanning and 9.04?"
date: 2009-04-13
forum: The Cafe
---

### Post by diablo75 on 2009-04-13
I recently ordered a laptop off ebay that has a fingerprint scanner.  So naturally I wanted to find out if I'd be able to use this nifty feature in Ubuntu, and someone I got a response from was under the impression that it would be in Jaunty because it's a part of GNOME 2.26.  But those who are using the Beta of Jaunty say it's not working out of the box for some reason.

So I was just curious if anyone knows the latest on development for getting this feature to work out of the box on Ubuntu?  I'm under the impression that there is a good chunk of development yet to be done (it would be worth the wait to see a, "Looks like you have a fingerprint sensor!  Would you like to set it up now?" prompt appear during upgrade/install).

---

### Post by perce on 2009-04-13
Try looking at the System 76 forums: they have models with fingerprint scanner and are working on it.

---

### Post by 23meg on 2009-04-13
[QUOTE=diablo75]I recently ordered a laptop off ebay that has a fingerprint scanner. So naturally I wanted to find out if I'd be able to use this nifty feature in Ubuntu, and someone I got a response from was under the impression that it would be in Jaunty because it's a part of GNOME 2.26. But those who are using the Beta of Jaunty say it's not working out of the box for some reason.[/QUOTE]

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083)

[QUOTE=diablo75](it would be worth the wait to see a, "Looks like you have a fingerprint sensor! Would you like to set it up now?" prompt appear during upgrade/install).[/QUOTE]

You'll never see such a prompt during an Ubuntu upgrade/install (hopefully). Your hardware will be autoconfigured and "just work" as long as it's supported. It would be a nightmare to have to endure such prompts for each piece of hardware during installation.

---

### Post by diablo75 on 2009-04-16
I found a bug report about this going on here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083)

It looks like they're waiting on another package to be updated, "libusb".  Anyone know when *that *might happen?

---

### Post by CJ Master on 2009-04-16
> **23meg said:**
> 
You'll never see such a prompt during an Ubuntu upgrade/install (hopefully). Your hardware will be autoconfigured and "just work" as long as it's supported. It would be a nightmare to have to endure such prompts for each piece of hardware during installation.

Though obviously, it has to be configured as too which fingerprints to accept...

---

### Post by 23meg on 2009-04-28
> **CJ Master said:**
> Though obviously, it has to be configured as too which fingerprints to accept...

The process of installing or upgrading an operating system is a scary, stressful one for most people, even technically adept users. A successful installer / upgrader design will ask as few questions as possible during it, and make sure each step that it's posing to the user is relevant. Asking for the user's *fingerprint* of all things is pretty out of place *during* such a process. 

> **diablo75 said:**
> I found a bug report about this going on here:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/346083)

It looks like they're waiting on another package to be updated, "libusb".  Anyone know when *that *might happen?

You may want to ask people involved with the upstream project directly, since it seems the code you want hasn't gone into an *upstream* release yet.

---

