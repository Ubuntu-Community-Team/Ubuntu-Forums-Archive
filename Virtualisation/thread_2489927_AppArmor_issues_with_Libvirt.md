---
title: "AppArmor issues with Libvirt"
date: 2023-08-15
forum: Virtualisation
---

### Post by johannes1985 on 2023-08-15
I have a fresh Ubuntu Server 22.04.3 and Debian 12.1.0 installed and updated. Along with Cockpit and Cockpit virtual machines on both tests machines.


I am getting the following errors and warning when looking at the log section in Cockpit:




```
Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to read AppArmor profiles list '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd






Failed to open file '/sys/kernel/security/apparmor/profiles': Permission denied libvirtd
```






The virtual machines start up and has no issues. However, the errors pop up after every reboot once I click the virtual machines section on Cockpit. These errors only show then, and not when I do NOT go to virtual machines section in Cockpit. So it seems to only start once you go to that section in Cockpit.


The /etc/apparmor.d/usr.sbin.libvirtd does have the line:


```

/sys/kernel/security/apparmor/profiles r,

```


My user has also been added to groups libvirt, kvm and sudo.


Also, when running the following command without sudo and not as root on the terminal, then I also get a permission denied. I checked the folder permissions and it does have read permissions and belong to the group root:


```

cat /sys/kernel/security/apparmor/profiles

```


Has anyone else experience this issue? Any solution to get it fixed with or without disabling AppArmor for KVM? or can the errors be safely ignored?




Thank you to the person who has a solution to this.

---

### Post by jeremy31 on 2023-08-15
Dupe of [https://ubuntuforums.org/showthread.php?t=2489926](https://ubuntuforums.org/showthread.php?t=2489926)
Closed

---

