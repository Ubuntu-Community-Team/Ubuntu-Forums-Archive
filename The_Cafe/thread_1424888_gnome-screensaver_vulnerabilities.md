---
title: "gnome-screensaver vulnerabilities"
date: 2010-03-08
forum: The Cafe
---

### Post by MasterNetra on 2010-03-08
> 
=========================================================== 
Ubuntu Security Notice USN-907-1             March 08, 2010
gnome-screensaver vulnerabilities 
CVE-2010-0285, CVE-2010-0422 
=========================================================== 

A security issue affects the following Ubuntu releases: 

Ubuntu 8.10 
Ubuntu 9.04 
Ubuntu 9.10 

This advisory also applies to the corresponding versions of Kubuntu, Edubuntu, and Xubuntu. 

The problem can be corrected by upgrading your system to the following package versions: 

Ubuntu 8.10:
  gnome-screensaver                        2.24.0-0ubuntu2.1

Ubuntu 9.04:
  gnome-screensaver                        2.24.0-0ubuntu6.1 

Ubuntu 9.10:
  gnome-screensaver                        2.28.0-0ubuntu3.5 

After a standard system upgrade you need to restart your session to effect the necessary changes. 

Details follow:

It was discovered that gnome-screensaver did not correctly lock all screens when monitors get hotplugged. An attacker with physical access could use this flaw to gain access to a locked session. (CVE-2010-0285) 

It was discovered that gnome-screensaver did not correctly handle keyboard grab when monitors get hotplugged. An attacker with physical access could use this flaw to gain access to a locked session. This issue only affected Ubuntu 9.10. (CVE-2010-0422)


Source:[http://www.ubuntu.com/usn/USN-907-1](http://www.ubuntu.com/usn/USN-907-1)

---

### Post by chriswyatt on 2010-03-08
I'm surprised that hadn't been discovered earlier.

---

