---
title: "WSL2 How to enable GUI authentication prompt?"
date: 2024-01-27
forum: Windows
---

### Post by ugnius40 on 2024-01-27
Hi,

Trying to run gedit like 
```

$gedit admin:///some/root/file

```
I'm getting error that admin editing is not supported. 
or
```

$ pkexec --disable-internal-agent "/usr/bin/gedit" "$@"
Error executing command as another user: No authentication agent found.

```
Polkit only authenticates in terminal, and for GUI apps it's broken anyway. 
I cannot find good info how to enable GUI authentication without dragging in full blown desktop on Xvnc.

```

> wsl --version
WSL version: 2.0.9.0Kernel version: 5.15.133.1-1
WSLg version: 1.0.59
MSRDC version: 1.2.4677
Direct3D version: 1.611.1-81528511
DXCore version: 10.0.25131.1002-220531-1700.rs-onecore-base2-hyp
Windows version: 10.0.22631.3007

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=22.04
DISTRIB_CODENAME=jammy
DISTRIB_DESCRIPTION="Ubuntu 22.04.3 LTS"

$ uname -r
5.15.133.1-microsoft-standard-WSL2

```

May be someone has some insights?

Thanks

---

### Post by yancek on 2024-01-28
This is not an Ubuntu or Linux problem, it is a windows problem.  WSL was initially designed to work without a GUI but can now be used with a GUI in some cases.  The link below to the microsoft site (creators of WSL) explains the limitations as well as  what you need and how to accomplish it.

  [https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)

---

### Post by ugnius40 on 2024-01-29
It seems I'm barking up the wrong tree.
That's exactly what guys at #windows-wsl IRC said - WSL was not designed for this, to spin up a proper VM or something would be more reasonable. 
I've dropped chasing this pkexec issue. 

Thanks for replying.

---

### Post by yancek on 2024-01-29
The link I posted above indicates which versions of windows should work for a GUI with WSL and explains the steps if interested.  If you already have WSL installed you will apparently need to uninstall it an reinstall.  Maybe other virtual software such as VirtualBox would be useful.

---

