---
title: "sl-modem-daemon upgrade error"
date: 2005-04-01
forum: Repositories &amp; Backports
---

### Post by Technoviking on 2005-04-01
I'm getting the following error when trying to apt-get dist-upgrade

root@pheonix:/home/dbasinge # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  sl-modem-daemon
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@pheonix:/home/dbasinge # apt-get install  sl-modem-daemon
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sl-modem-daemon: Depends: sl-modem-modules-new but it is not installable
E: Broken packages

It has been about 36 hour and still no sl-modem-modules-new package.

Mike

---

