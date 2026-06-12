---
title: "Virtualbox screen resolution 1920x1080 disappeared from the list"
date: 2014-04-28
forum: Virtualisation
---

### Post by yan4 on 2014-04-28
Hi,

I am running Ubuntu 12.10 and Virtualbox 4.1.18.

I have a VM guest running Windows 7 64 and it was working fine at 1920x1080 screen resolution.

This morning I was playing with the other resolutions at the guest window and suddenly I couldn't go back to the 1920x1080 anymore because it disappeared from the list.

I tried to reboot either the guest as well the host but the 1920x1080 resolution seems to be gone forever.

Any idea about what may happened? Any possible solution without to have to reinstall the whole stuff?

Thanks!

---

### Post by SeijiSensei on 2014-04-28
One thing you can try right away is installing or re-installing the [Extension Pack]("https://www.virtualbox.org/wiki/Downloads").  Make sure you use the right version.  The Extension Pack is pretty much mandatory to get the best resolutions available.  See if you can run 1920x1080 afterwards.

However, you should consider upgrading your Linux version to 14.04.  12.10 reached its "end-of-life" [this month](https://wiki.ubuntu.com/Releases).  Also your VirtualBox installation is quite old; the current version is 4.3.10.  After you upgrade Linux, I recommend obtaining VB from its own repository; follow the instructions [here](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions).  There isn't a version for Trusty yet, so use the entry for Saucy. It's working fine on my Kubuntu 14.04 machine.

Afterwards download and install the Extension Pack for VB 4.3.

---

### Post by slickymaster on 2014-04-28
In the main VirtualBox window navigate to File -> Preferences -> Display -> change the value of 'Maximum Guest Screen Size' to **Hint**. Once that done you can change the width and height on the boxes bellow to whatever resolution you have for your desktop or anything else you want.
You need to use the full screen toggle (host+F) to go into full screen. Anything else will not give the full resolution.

---

### Post by yan4 on 2014-04-28
Slickymaster, I don't have a 'Display' option in my Preferences. Maybe it is a thing of Virtualbox newer versions?

Seijisensei, I will try to reinstall the Extension Pack. I believe that if I reinstall the whole Virtualbox it may fix the problem I just didn't want to do that. But if I had to I will update my Virtualbox to a newer version and see what happens.

I will have news very soon!

Thanks for both.

:)

---

### Post by jon43 on 2014-04-28
In Windows 7, I always have to install the Guest Extentions iso inside of the machine to get it to run full 1920x1080.

---

### Post by yan4 on 2014-04-28
Yeah... I don't know what happened. It was working and suddenly it wasn't there anymore. By the way, I have the Extension Pack and Guest Extensions installed...

Anyway, reinstall the Extension Pack didn't fix it. Then I tried to install the Virtualbox 4.3.10 but it won't because there is a lot of missing dependencies. I removed my Virtualbox and will try to reinstall it to see if the 1920x1080 comes back.

Also I am downloading an ISO of Ubuntu 14.04 to see what happens in the next...

:roll:

---

