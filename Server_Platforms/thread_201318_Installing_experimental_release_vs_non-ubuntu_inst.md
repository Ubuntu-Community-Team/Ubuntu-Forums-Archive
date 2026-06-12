---
title: "Installing experimental release vs non-ubuntu install"
date: 2006-06-21
forum: Server Platforms
---

### Post by kip on 2006-06-21
I want to install egroupware 1.2.  Currently Ubuntu only has 1.09.  It appears I can either download the installation from egroupware directly, or install it from a debian experimental release.  Since I am new to Ubuntu (and Debian) I would like general advice about whether it's better to install releases direclty from a company, or to use a Debian experimental release.

One of my concerns with using the company's installation directly is it configures things differently than Ubuntu does.  Directory structure is different, for example.  That would mean I'd never be able to do updates with Ubuntu, so I'm less enthusiastic about this approach.

Anyway, I'm just wondering if others have ran into this type of decision, and which way they went, and what other considerations I should take into account.

Thanks

---

### Post by lamego on 2006-06-22
I had this kind of decisions with other software packages. If you believe there will be a version upgrade for Ubuntu then it is preferable to wait to make sure the upgrades will be easier to manager, however there are certain packages which don't get update often, if that's the case and you really need some of the features on the newer version you don't have another choice besides doing a manual install.
Anyway after the first manual install it will be easy to upgrade, usually you just need to write down some unusual steps that you may on the next upgrades.
Also don't forget to uninstall the ubuntu package version to avoid conflicts with your manual installation.

Hope this helps

---

### Post by kwalker on 2006-07-15
I am struggling with this same choice.  There is a discussion going on about it at:

[http://forum.egroupware.org/viewtopic.php?t=30396](http://forum.egroupware.org/viewtopic.php?t=30396)

If I have it right, following either the svn method or the other method discussed there, means that the package will not be upgradeable with apt-get afterwards.  Or is it worse than that, will apt-get get confused by the non debian upgrade?

There are some recent changes to the eGroupware package, in fact some that are expected in the  next few days.  Am I guessing right that for that to get into the ubuntu repository waits for a debian maintainer to do a new deb and then for it to get into the debian repositories and then for 6.10 or whatever it will be of kubuntu to come out?

---

