---
title: "UFW not installing due to error - 9.04"
date: 2009-08-12
forum: Server Platforms
---

### Post by Vinni3 on 2009-08-12
My friend recently brought a dedicated server for his site, and asked the host to install Ubuntu Server 9.04 for him. He then proceded to install ehcp (via 
```
wget [www.ehcp.net/download](www.ehcp.net/download)
tar -zxvf ehcp_latest.tgz
cd ehcp
./install.sh
# 
```
and updated the system. He needed help to set up ufw, so I executed apt-get install ufw under root. It then chucked up this error:

```

root@ks364771:~# apt-get install ufw
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ufw: Depends: python (>= 2.5) but it is not going to be installed
       Depends: python-central (>= 0.6.7) but it is not going to be installed
E: Broken packages

```

TIA.

---

### Post by cariboo on 2009-08-12
Ufw is installed by default, you shouldn't need to install it. Unless it was a typo and you meant gufw.

---

### Post by Vinni3 on 2009-08-12
That's odd - ufw is not installed on the server by defult. Everytime I try to setup the firewall, the ufw commands are not found. :S

EDIT:
OK, so he reformatted it with nothing on (ie. no updates ect), but now, ufw is apprently
Package ufw is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ufw has no installation candidate

EDIT 2: Ignore, I fixed it. :D

---

