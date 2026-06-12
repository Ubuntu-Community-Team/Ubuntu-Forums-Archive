---
title: "condor on ubuntu precise"
date: 2012-04-26
forum: Server Platforms
---

### Post by surfer on 2012-04-26
just for your information:

condor has been [removed]("https://bugs.launchpad.net/ubuntu/+source/condor/+bug/919671") (for the moment) from the repository.

but it can be easily installed (tried it on amd64 only):

- download condor-7.6.6-1-deb_6.0_amd64.deb from [http://research.cs.wisc.edu/condor/](http://research.cs.wisc.edu/condor/)
- $ sudo apt-get install  libc6-i386 libvirt0 libapparmor1 libnuma1 libxenstore3.0
- $ sudo dpkg -i condor-7.6.6-1-deb_6.0_amd64.deb

if your network is properly configured (condor insists on a domain name) and your condor_config is correct, everything works just fine!

---

