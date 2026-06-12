---
title: "unattended upgrades with ubuntuzilla"
date: 2013-10-23
forum: Ubuntuzilla
---

### Post by ColinTempler on 2013-10-23
Hello,
I'm trying to get unattended upgrades to install automatic updates from ubuntuzilla repos under Debian Wheezy.
I've configured **/etc/apt/apt.conf.d/50unattended-upgrades**:
```

Unattended-Upgrade::Origins-Pattern {
      "o=Debian,a=stable";
      "o=Debian,a=stable-updates";
      "origin=Debian,archive=stable,label=Debian-Security";
      "origin=Daniel Folkinshteyn,archive=Stable";
};

```
And here's the output of **unattended-upgrades --debug**:
```

Initial blacklisted packages: 
Starting unattended upgrades script
Allowed origins are: ['o=Debian,a=stable', 'o=Debian,a=stable-updates', 'origin=Debian,archive=stable,label=Debian-Security', 'origin=Daniel Folkinshteyn,archive=Stable']
Checking: thunderbird-mozilla-build (["<Origin component:'main' archive:'stable' origin:'Daniel Folkinshteyn' label:'Mozilla .debs packaged by Ubuntuzilla' site:'downloads.sourceforge.net' isTrusted:True>"])
pkgs that look like they should be upgraded: 
Fetched 0 B in 0s (0 B/s)                                                      
fetch.run() result: 0
blacklist: []
InstCount=0 DelCount=0 BrokenCout=0
No packages found that can be upgraded unattended

```

Am I missing something?

---

### Post by nanotube on 2013-10-25
Hi ColinTempler,

My guess is that you have not installed any ubuntuzilla packages. The packages in the ubuntuzilla repo are called 'firefox-mozilla-build', 'thunderbird-mozilla-build', and 'seamonkey-mozilla-build'. So after you add the repo, you must install the package you want, before the auto-updater will take over.

Hope that helps - let know how it goes.

---

### Post by ColinTempler on 2013-10-25
Thanks!
Well what I've downloaded thunderbird-mozilla-build_24.0-0ubuntu1_amd64.deb, one version behind the last, and installed it.
After this I ran the unattended-upgrades and was expecting the it to be updated.
Does it somehow detect that the thunderbird package has been installed directly ?

---

### Post by nanotube on 2013-10-25
Hi,

afaik, when you install a .deb directly, it should do pretty much the same stuff as when you get from a repository. but... i'm not sure how unattended-upgrades works, exactly, so... hard to say.

try to manually run apt-get update, see if it tells you that thunderbird-mozilla-build has a new version available?

---

