---
title: "lxc upgrading"
date: 2013-12-29
forum: Virtualisation
---

### Post by grouppict on 2013-12-29
Trying to upgrade the lxc version from 0.7.5 to 0.8.0. Executed following command :
  apt-get install lxc
  But it didnt work the package is still 0.7.5.
  apt-get install lxc=0.8.0
  Gives error saying 
  E: Version '0.8.0' for 'lxc' was not found
  How to upgrade it to next version (0.8.0 the specific)? Please help! Thanks!

---

### Post by TheFu on 2014-01-01
Which Ubuntu version are you running?

Are you certain the repository has a newer release?

May need a PPA (assuming you trust the PPA creator) to run unknown code on your system(s)
or might need to install from source code (please avoid this).

**sudo apt-get update && sudo apt-get dist-upgrade**

are all most people should have to do to maintain a system. 

Which specific release of lxc (or any package) that is available for any specific Ubuntu release can be found by googling. This was found: [https://launchpad.net/ubuntu/+source/lxc](https://launchpad.net/ubuntu/+source/lxc) 
See how different Ubuntu releases have different LXC releases?  If you are on 12.04, then do not expect any newer LXC releases without a PPA.

Anyway, I hope this helps.

---

