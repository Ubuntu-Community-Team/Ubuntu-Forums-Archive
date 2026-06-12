---
title: "SElinux installed and removed. Apparmor doesn't seem fully installed"
date: 2018-05-24
forum: Security
---

### Post by rsteinmetz70112 on 2018-05-24
I hope this is the right place for this

On one of my systems which has been upgraded through multiple LTS versions I began having problems with error messages related to SElinux. I was puzzled why it was installed. I thought perhaps it was a dependency for something else.  In any event I removed it, except for /sys/fs/selinux. I also autoremoved it's related packages. That solved my original problem but now I have a couple of questions.

**Should I remove /sys/fs/selinux manually?** It seems like it has no use and is merely taking up space.

In checking against another system I tested what packages would be installed If I installed SElinux on that system. I noticed it would uninstall apparmor packages.
```
~# apt-get install selinux
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following package was automatically installed and is no longer required:
  libapparmor-perl
Use 'sudo apt autoremove' to remove it.
The following additional packages will be installed:
  checkpolicy libapol4 libauparse0 libqpol1 policycoreutils python-audit
  python-ipy python-selinux python-semanage python-sepolgen python-sepolicy
  python-setools selinux-policy-dev selinux-policy-ubuntu selinux-utils
  setools
Suggested packages:
  setools-gui
The following packages will be REMOVED:
  apparmor apparmor-easyprof-ubuntu click-apparmor mysql-server
  mysql-server-5.7 python3-apparmor-click snap-confine snapd
The following NEW packages will be installed:
  checkpolicy libapol4 libauparse0 libqpol1 policycoreutils python-audit
  python-ipy python-selinux python-semanage python-sepolgen python-sepolicy
  python-setools selinux selinux-policy-dev selinux-policy-ubuntu
  selinux-utils setools
0 upgraded, 17 newly installed, 8 to remove and 68 not upgraded.
Need to get 6,913 kB of archives.
After this operation, 35.2 MB disk space will be freed.
```

Going back to the original system I tested installing apparmor and got the following. 

```
# apt install apparmor
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  libapparmor-perl
Suggested packages:
  apparmor-profiles apparmor-profiles-extra apparmor-docs apparmor-utils
The following NEW packages will be installed:
  apparmor libapparmor-perl
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 482 kB of archives.
After this operation, 1,906 kB of additional disk space will be used.
```

[B]It appears that apparmor is not installed. I feel it should be installed but if I do at this point what issues am I likely to run into?
[/B]

---

### Post by TheFu on 2018-05-24
/sys is a pseudo file system. It isn't taking any space.
Check out the* file system hierarchy standards *to learn what goes where. Google will find it.

---

