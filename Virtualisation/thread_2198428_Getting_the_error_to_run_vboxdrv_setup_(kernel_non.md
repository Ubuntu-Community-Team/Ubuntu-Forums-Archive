---
title: "Getting the error to run vboxdrv setup (kernel non-match) despite successful compile"
date: 2014-01-08
forum: Virtualisation
---

### Post by 6tr6tr on 2014-01-08
I got the error that tells me to run "/etc/init.d/vboxdrv setup" because of VB's kernel modules not matching this version of VirtualBox (it's the latest version), so I ran that (with sudo) and it went successfully with all green "done" messages. But I'm still getting this error. I even tried restarting! What can I do to fix this?

Even after installing "kernel-devel", "kernel-source", etc and recompiling, it still doesn't work!

---

### Post by 6tr6tr on 2014-01-08
Discovered the problem. While VirtualBox was the newest version, the OS already had installed "virtualbox-guest-kmp-default", "virtualbox-guest-tools", "virtualbox-guest-x11" for version 4.2. I uninstalled those.

---

