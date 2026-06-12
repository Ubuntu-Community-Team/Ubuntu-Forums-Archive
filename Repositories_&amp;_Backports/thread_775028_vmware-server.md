---
title: "vmware-server"
date: 2008-04-29
forum: Repositories &amp; Backports
---

### Post by rabid9797 on 2008-04-29
when can we expect to see a version for hardy in the canonical repos? :)

---

### Post by knarf on 2008-04-30
With VMware (server or otherwise) my experience is that it is better to use the version published on VMware's own site than to rely on the Ubuntu-packaged version. While VMware does not publish a .deb directly suitable for installation on Debian-derived distributions it only takes an alien session to rectify this omission:

```
fakeroot alien name_of_rpm_package.rpm
```

It will complain about not translating the pre/post install/remove scripts, ignore that as those scripts are tailored to rpm-based systems. Alien produces an installable .deb. Install it. Install the latest/greatest vmware-any-any-v???.tgz to get those modules to compile with recent kernels (currently the most up to date versions seem to be at [http://groups.google.com/group/vmkernelnewbies/files](http://groups.google.com/group/vmkernelnewbies/files)). Installing the latter will also configure VMware.

By the way, the reason why I use the 'original' instead of the Ubuntu-packaged version is that I have had configuration- and stability-problems with the latter. The Ubuntu-packaged version was also not kept up to date with new releases from VMware.

---

