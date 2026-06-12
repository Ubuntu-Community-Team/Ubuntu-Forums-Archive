---
title: "install Ubuntu Server in vmware (as guest)"
date: 2006-06-07
forum: Server Platforms
---

### Post by Michael Kofler on 2006-06-07
I tried to install Ubuntu Dapper Server (ubuntu-server-i386.iso) in VMware workstation (host=Windows, guest=Ubuntu Server)

the installation completed, but after the reboot the system hanged after de-compressing the kernel-image (CPU usage 100%)

I also tried to install a Server from a normal Ubuntu iso image ('install a server' in start menu); this worked fine

so I guess the server iso has an other kernel than the normal ubuntu iso, and the server kernel is in some way incompatible with vmware

any ideas? is it possible to choose another kernel during installation?

---

### Post by rbalfour on 2006-06-07
there is a workaround.

[http://www.ubuntuforums.org/showthread.php?t=187633&highlight=vmware+server](http://www.ubuntuforums.org/showthread.php?t=187633&highlight=vmware+server)

---

