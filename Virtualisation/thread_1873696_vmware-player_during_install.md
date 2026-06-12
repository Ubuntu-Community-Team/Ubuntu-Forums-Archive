---
title: "vmware-player during install"
date: 2011-11-01
forum: Virtualisation
---

### Post by lime4x4 on 2011-11-01
Trying to install wmware player 4.0 in 11:10 64 bit. When i start the install process it just hangs. This what is in the terminal screen

john@john-desktop:~/Downloads$ gksu bash VMware-Player-4.0.0-471780.x86_64.bundle
Extracting VMware Installer...done.
You must accept the VMware OVF Tool component for Linux End User

---

### Post by dcstar on 2011-11-02
> **lime4x4 said:**
> Trying to install wmware player 4.0 in 11:10 64 bit. When i start the install process it just hangs. This what is in the terminal screen

john@john-desktop:~/Downloads$ **gksu bash **VMware-Player-4.0.0-471780.x86_64.bundle
Extracting VMware Installer...done.
You must accept the VMware OVF Tool component for Linux End User

Why????

```
sudo ./VMware-Player-4.0.0-471780.x86_64.bundle
```

---

### Post by lime4x4 on 2011-11-02
john@john-desktop:~$ sudo ./VMware-Player-4.0.0-471780.x86_64.bundle
[sudo] password for john: 
sudo: ./VMware-Player-4.0.0-471780.x86_64.bundle: command not found

---

### Post by fjgaude on 2011-11-03
Change your prompt to the directory where the .bundle file is.

---

### Post by Kobin on 2012-01-15
Just if any one else finds this thread I will make the solution to this problem clear:

If you run the VmPlayer installer with:
```
gksudo bash ./VMware-Player-4.0.1-528992.x86_64.bundle 
```
Then the installer will hang when waiting for the user to accept the OVF license.
Use the following instead:
```
sudo ./VMware-Player-4.0.1-528992.x86_64.bundle 
```
Be sure to have made the installer executable before running it. This can done by doing the following:
```
chmod +rx VMware-Player-4.0.1-528992.x86_64.bundle
```

---

