---
title: "The unknown vBox (site) download"
date: 2015-06-05
forum: Virtualisation
---

### Post by v3.xx on 2015-06-05
I wanted to set up virtualbox on a 15.10 install.  I always install from the site, but no wily package for it yet, so down at the bottom of the linux download list is ..
> All distributions  i386 |  AMD64 
So I figure why not and loaded it up.  Got it working, but I wonder what ubuntu specific packages are left out of this build.  Anyone know anything about this download?  I would like to know more about it.

[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by SeijiSensei on 2015-06-06
It appears to be a script that contains an embedded image of the VirtualBox binary.  I doubt anything is "left out."  The different package options should all include basically the same software but configured to use the preferred packaging format for each distribution (.deb, RPM, etc.).  Some distributions might put certain files in different locations, but even that's pretty uncommon these days.

It should be comparable to installing a copy of Firefox directly from Mozilla rather than the version packaged for Ubuntu.  In that case you download and extract the binary to some directory in your path like $HOME/bin.

I generally prefer to follow the instructions for "Debian-based distributions" on that page.  I'd use the Vivid repository since that's the closest one to 15.10.  I've followed that path for development versions or for recent releases where Oracle had not yet packaged a version for that release.

---

### Post by v3.xx on 2015-06-06
Thanks for the reply.

It runs fine, just never used it before.
> I'd use the Vivid repository since that's the closest one to 15.10.
I was going to do that, but I thought this would be a good time to check out this download.
The color and font looks a little washed out and first thought was maybe a missing Qt or gtk setting or package with this install.  Something I'm not real concerned about, more of a curiosity about this download.

Anyhow, a good enough answer for me.  I say time to move on.  Thanks

---

### Post by howefield on 2015-06-06
The current version is also in the Wily repository.

---

### Post by v3.xx on 2015-06-06
> **howefield said:**
> The current version is also in the Wily repository.
Yep

I really do not know if it even applies anymore, but the site download just seems to work a little better.

---

### Post by SeijiSensei on 2015-06-06
> **howefield said:**
> The current version is also in the Wily repository.

You are probably talking about the Ubuntu repository rather than Oracle's which I prefer to use since it is routinely updated when new point releases come out.  That repository is at [http://dlc-cdn.sun.com/virtualbox/4.3.28/](http://dlc-cdn.sun.com/virtualbox/4.3.28/) and has no version for Wily as of yet.  It probably won't have one until Wily is officially released this fall.

---

