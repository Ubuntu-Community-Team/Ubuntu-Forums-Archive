---
title: "Latest update-notifier-common upgrade 3.192.30.4 installs alsa packages - why?"
date: 2021-01-20
forum: Server Platforms
---

### Post by ameinild on 2021-01-20
Hi. 
I just wanted to see if someone can explain what's going on. With the latest unattended-upgrade, the upgrade of the package update-notifier-common also installed a number of packages, which I really don't understand why are installed on a server. This is the [FONT=courier new]/var/log/apt/history.log[/FONT][FONT=verdana] entry:
[/FONT]
```
Start-Date: 2021-01-20  06:52:55
Commandline: /usr/bin/unattended-upgrade
Install: alsa-topology-conf:amd64 (1.2.2-1, automatic), alsa-ucm-conf:amd64 (1.2.2-1ubuntu0.5, automatic), python3-xkit:amd64 (0.5.0ubuntu4, automatic), libpciaccess0:amd64 (0.16-0ubuntu1, automatic), libasound2-data:amd64 (1.2.2-2.1ubuntu2.3, automatic), alsa-utils:amd64 (1.2.2-1ubuntu2, automatic), ubuntu-drivers-common:amd64 (1:0.8.4~0.20.04.3, automatic), libgomp1:amd64 (10.2.0-5ubuntu1~20.04, automatic), libasound2:amd64 (1.2.2-2.1ubuntu2.3, automatic), libsamplerate0:amd64 (0.1.9-2, automatic), libatopology2:amd64 (1.2.2-2.1ubuntu2.3, automatic), libfftw3-single3:amd64 (3.3.8-2ubuntu1, automatic)
Upgrade: update-notifier-common:amd64 (3.192.30.3, 3.192.30.4)
End-Date: 2021-01-20  06:53:02
```

Why on earth would I need a bunch of Alsa packages on my server??? I think the main culprit here is the ubuntu-drivers-common package, which installs the rest (I figured this out by using [FONT=courier new]apt-cache rdepends --installed alsa-utils[/FONT]). Now, I can live with this, but I just find it very odd. I should mention that I got rid of a bunch of alsa packages in the first place by removing the normal vim package.

So a couple of questions come to mind:

1) Why are alsa/sound driver packages automatically installed on a server in the first place?
2) Would it be safe to autoremove the package ubuntu-drivers-common, which I then believe would remove all the unneeded packages?

And no, this really isn't a huge deal - it's just the principle that I don't understand why a server would need sound drivers to be automatically installed.

---

