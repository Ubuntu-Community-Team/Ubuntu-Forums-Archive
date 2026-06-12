---
title: "Ubuntu 13.10 Issue - error remove kernel 3.8.0-24"
date: 2013-06-09
forum: Ubuntu Development Version
---

### Post by TheMixtureMedia on 2013-06-09
Hey there I am getting this error when I try to remove kernel 3.8.0-24

E: linux-headers-3.8.0-24-generic: unable to securely remove '/usr/src/linux-headers-3.8.0-24-generic/include/config/x86/mce/intel.h': Not a directory

Ubuntu is forcing me to remove this but I have this error.

---

### Post by deadflowr on 2013-06-09
What kernel are you on now?

```
uname -a
```

The current saucy kernel is 3.9.0.4.blahblahblah.

You can try uninstalling the old kernels through synaptic.

---

### Post by oldos2er on 2013-06-09
Moved to Ubuntu +1

---

### Post by TheMixtureMedia on 2013-06-09
Hey there right now my kernel version is 3.9.0-4-generic and I tried to uninstall via synaptic and it will not let me. I also tried again to install new updates and it will not let me with out uninstalling the old kernel.

---

### Post by TheMixtureMedia on 2013-06-09
Hey there I figured out the issue [http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1)


up vote
5
down vote
[http://www.iasptk.com/ubuntu-fix-broken-package-best-solution](http://www.iasptk.com/ubuntu-fix-broken-package-best-solution)

After trying

sudo dpkg --configure -a
and

sudo apt-get install -f
the problem of a broken package still exist the solution is to edit the dpkg status file manually.

sudo gedit /var/lib/dpkg/status  
(you can use vi or nano instead of gedit)

Locate the corrupt package, and remove the whole block of information about it and save the file.

shareimprove this answer
answered Oct 3 '12 at 17:18

ptheo
55616
Editing the status file was the solution! Thank you so much! :D &#8211; delha Oct 4 '12 at 8:38
Same here, got it fixed by editing the status file. +1 &#8211; AnPel Jan 6 at 10:57
Thanks! I managed to fix that problem too. +1 &#8211; Stasel Apr 12 at 13:03

---

### Post by cariboo on 2013-06-09
I jailed a duplicate post.

---

