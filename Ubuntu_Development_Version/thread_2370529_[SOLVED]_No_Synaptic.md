---
title: "[SOLVED] No Synaptic?"
date: 2017-09-04
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-09-04
Looking in today's daily live. Updated it and tried to install Synaptic.
> # apt update
Ign:1 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Alpha amd64 (20170902) artful InRelease
Hit:2 cdrom://Ubuntu 17.10 _Artful Aardvark_ - Alpha amd64 (20170902) artful Release
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful InRelease [237 kB]               
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) artful-security InRelease              
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful-updates InRelease                
Fetched 237 kB in 0s (409 kB/s)                   
Reading package lists... Done
Building dependency tree       
Reading state information... Done
38 packages can be upgraded. Run 'apt list --upgradable' to see them.

> # apt install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate


Tried with Software,

---

### Post by ventrical on 2017-09-04
What desktop?

---

### Post by deadflowr on 2017-09-04
Is universe enabled?

---

### Post by Chanath on 2017-09-04
> **deadflowr said:**
> Is universe enabled?
It wasn't. Enabled it and got it installed. Thanks.:)

@ ventrical

I'm trying out Ubuntu 17.10, the default one.

---

### Post by ventrical on 2017-09-04
> **Chanath said:**
> It wasn't. Enabled it and got it installed. Thanks.:)

@ ventrical

I'm trying out Ubuntu 17.10, the default one.

I'll look forward your reports. If you test that as well as you test unity7, it can only make it better :)

Regards..

---

