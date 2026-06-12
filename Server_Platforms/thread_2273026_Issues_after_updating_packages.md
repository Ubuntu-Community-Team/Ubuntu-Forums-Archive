---
title: "Issues after updating packages"
date: 2015-04-10
forum: Server Platforms
---

### Post by phill2 on 2015-04-10
As something of a Ubuntu & Linux newb I'm in serious need of some help.

Ive set-up a Ubuntu server on an Azure VPS, and have installed Webmin & Virtualmin on the box so as to assist with the general maintenance of the server but mostly so as to make setting up new web hosting account for my clients websites. 

Every so often Webmin will tell me that there are new packages(upgrades) available. However, at some point the installation of upgrades will start to fail with the an error along the lines of this:

```
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-cloud-tools-common (3.13.0-49.81) ...
start: Job failed to start
invoke-rc.d: initscript hv-kvp-daemon, action "start" failed.
dpkg: error processing package linux-cloud-tools-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-cloud-tools-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Now, I really don't know how to address fixing this. I've tried running 'sudo apt-get install -f' but that returns the same error. I've also tried doing an apt-get upgrade, but the same happens again.

I know from experience, that after a while this issue start leading to all sort of additional errors when it comes to doing any other updates/upgrades/installs. Eventually I end up with a server that no longer works in some capacity and I'm left with no option but to build a new server on Azure and migrate all the hosting / virtualmin data.

Any help on fixing this &/or working out why this keeps happening, will be greatly appreciated.

P.s. Im on Ubuntu 14.04.2 LTS which was upgraded from a fresh install of Ubuntu 12.x due to the fact that 14.x doesnt seem to have quotas.

Thanks in advance.

---

### Post by slickymaster on 2015-04-10
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by phill2 on 2015-04-14
bump.... Anyone??? Pleaaaassseee!

---

### Post by Bashing-om on 2015-04-14
phill2; Humm ...

Have you tried to re-install 'linux-cloud-tools-common' ?
```

sudo apt-get install --reinstall linux-cloud-tools-common

```

See what results and what the package manager advises.

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe more work to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

