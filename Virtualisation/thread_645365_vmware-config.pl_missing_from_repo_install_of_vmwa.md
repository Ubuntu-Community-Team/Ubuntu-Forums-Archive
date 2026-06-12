---
title: "vmware-config.pl missing from repo install of vmware"
date: 2007-12-20
forum: Virtualisation
---

### Post by rodda on 2007-12-20
I took a chance and opted to install vmware-server from the 'partner' repos of Ubuntu instead of using the TAR binary from VMWare.  Question is: how do I reconfigure the networking?  I can't seem to locate vmware-config.pl and 'sudo dpkg-reconfigure vmware-server' doesn't seem to do the trick.  

Any help would be appreciated.

---

### Post by toobuntu on 2007-12-20
When installed from the partners repo, the script can be found here:
/usr/bin/vmware-config-network.pl

When compiling from a tarball downloaded from the VMware website, the script can be found here:
/usr/bin/vmware-config.pl

---

### Post by rodda on 2007-12-20
Many thanks.  Are other changes similar to this documented in a 'readme' anywhere?

---

### Post by toobuntu on 2007-12-20
I am not aware of one.  You could try the wiki or searching other forum posts.  My guess is that the changes made by the Ubuntu packagers would be discussed somewhere in the mailing lists.  When I first needed it, I only found the script by:

```
locate vmware-config
```

and then noticed the name change.

---

