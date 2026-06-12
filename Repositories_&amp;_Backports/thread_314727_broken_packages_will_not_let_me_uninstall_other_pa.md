---
title: "broken packages will not let me uninstall other packages"
date: 2006-12-08
forum: Repositories &amp; Backports
---

### Post by fakie_flip on 2006-12-08
```
brad@Brads-desktop:~$ sudo aptitude purge nvidia-glx nvidia-kernel-common
Reading package lists... Done 
Building dependency tree... Done
Reading extended state information 
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  linux-restricted-modules-2.6.15-23-386 
  linux-restricted-modules-2.6.15-27-386
The following packages have been kept back: 
  gnupg
The following packages will be REMOVED:
  nvidia-glx{p} nvidia-kernel-common{p}
0 packages upgraded, 0 newly installed, 2 to remove and 1 not upgraded. 
Need to get 0B of archives. After unpacking 12.7MB will be freed.
The following packages have unmet dependencies:
  linux-restricted-modules-2.6.15-23-386: Depends: nvidia-kernel-common but it i                                             s not installable 
  linux-restricted-modules-2.6.15-27-386 : Depends: nvidia-kernel-common but it i                                             s not installable
Resolving dependencies...
The following actions will resolve these dependencies: 

Keep the following packages at their current version:
nvidia-kernel-common [20051028+1 (dapper, now)]

Score is 1

Accept this solution? [Y/n/q/?]
brad@Brads-desktop:~$
```
I pushed control and c to exit aptitude. How can I fix this and remove those packages?

---

### Post by devnulljp on 2006-12-08
Easiest way, use synaptic, Edit->Fix broken packages

---

### Post by robbie75 on 2006-12-08
Or, if you are in the same situation I experienced
till yesterday (you can find a thread started by me
just about aptitude problem) you'll notice that
apt-get and synaptic will not complain about broken
dependencies at all, so it was an aptitude problem
for me: simply remove by aptitude the broken packages,
then reinstall it and everything will be ok...at least
for me it worked ;)

you can take a look here:
[http://www.ubuntuforums.org/showthread.php?t=313487](http://www.ubuntuforums.org/showthread.php?t=313487)

---

