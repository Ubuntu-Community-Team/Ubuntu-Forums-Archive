---
title: "I upgrade and now this happens"
date: 2015-01-24
forum: Ubuntu/Debian BASED
---

### Post by nazareno2 on 2015-01-24
Hi everybody, i have this error when i try to install with apt-get install:
apt-get install php5-cgi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libnm-gtk0 : Breaks: network-manager-gnome (< 0.9.10.0) but 0.9.4.1-5 is to be installed
 ppp : Breaks: network-manager (< 0.9.8.8-7~) but 0.9.4.0-10 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I have Kali system. Please help me.

---

### Post by ian-weisser on 2015-01-24
Please try the following two commands, and post the entire output here:
```
apt-cache policy libnm-gtk0
apt-cache policy ppp
```

---

### Post by oldos2er on 2015-01-25
Moved to Other OS Support and Projects.

[https://forums.kali.org/](https://forums.kali.org/)

---

