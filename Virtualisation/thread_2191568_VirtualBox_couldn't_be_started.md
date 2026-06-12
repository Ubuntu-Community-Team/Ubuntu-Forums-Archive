---
title: "VirtualBox couldn't be started"
date: 2013-12-03
forum: Virtualisation
---

### Post by satimis on 2013-12-03
Hi all,

Ubuntu 12.04 host 64bit
Virtualbox 4.1.12

Today after running;
$ sudo apt-get update and && sudo apt-get upgrade

encountered 2 problems

1)
login problem
host user satimis couldn't be found only guest there.

I fixed it with;
renaming .Xauthority as .Xauthority.BAK

and ran;
$ sudo apt-get -reinstall xorg

now
2)
VirtualBox couldn't be started

$ virtualbox```

Error opening file for reading: Permission denied
```

$ ls -als /usr/bin/virtualbox```

0 lrwxrwxrwx 1 root root 27 Oct  4 04:18 /usr/bin/virtualbox -> ../share/virtualbox/VBox.sh

```

$ sudo chown satimis:satimis /usr/bin/virtualbox

$ ls -als /usr/bin/virtualbox```

0 lrwxrwxrwx 1 root root 27 Oct  4 04:18 /usr/bin/virtualbox -> ../share/virtualbox/VBox.sh

```
owner couldn't be changed

$ sudo gedit /etc/group```

change:-
users:x:100:
as:-
users:x:100:satimis

change:-
lp:x:7:
as:-
lp:x:7:satimis

satimis already in:
vboxusers:x:125:satimis

satimis already in:
vboxusers:x:125:satimis

```

But still failed.

Warning:```

Failed to open a session for the virtual machine deb710dkc8_01.

Implementation of the USB 2.0 controller not found!

Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

```

Download virtualbox-4.1_4.1.28-89849~Ubuntu~precise_amd64.deb
on;
[https://www.virtualbox.org/wiki/Download_Old_Builds_4_1](https://www.virtualbox.org/wiki/Download_Old_Builds_4_1)

$ sudo dpkg -i virtualbox-4.1_4.1.28-89849~Ubuntu~precise_amd64.deb 
```

Selecting previously unselected package virtualbox-4.1.
dpkg: considering removing virtualbox in favour of virtualbox-4.1 ...
dpkg: no, cannot proceed with removal of virtualbox (--auto-deconfigure will help):
 virtualbox-qt depends on virtualbox (= 4.1.12-dfsg-2ubuntu0.5)
  virtualbox is to be removed.
dpkg: regarding virtualbox-4.1_4.1.28-89849~Ubuntu~precise_amd64.deb containing virtualbox-4.1:
 virtualbox-4.1 conflicts with virtualbox
  virtualbox (version 4.1.12-dfsg-2ubuntu0.5) is present and installed.
dpkg: error processing virtualbox-4.1_4.1.28-89849~Ubuntu~precise_amd64.deb (--install):
 conflicting packages - not installing virtualbox-4.1
Errors were encountered while processing:
 virtualbox-4.1_4.1.28-89849~Ubuntu~precise_amd64.deb

```


Please help.  TIA

B.R.
satimis

---

### Post by jdeca57 on 2013-12-03
> 
Failed to open a session for the virtual machine deb710dkc8_01.

Implementation of the USB 2.0 controller not found!

I'm a bit at loss here. It's possible to either go to settings and disable the USB support or go to the site and download the extensions and have (after agreeing to their license) said support.
- That error message indicates that VirtualBox is installed and works, so why a downgrade?

---

### Post by satimis on 2013-12-04
> **jdeca57 said:**
> I'm a bit at loss here. It's possible to either go to settings and disable the USB support or go to the site and download the extensions and have (after agreeing to their license) said support.
- That error message indicates that VirtualBox is installed and works, so why a downgrade?
Hi,

Problem was solved by download and installing Oracle VM VirtualBox Extension Pack.

Thanks

satimis

---

