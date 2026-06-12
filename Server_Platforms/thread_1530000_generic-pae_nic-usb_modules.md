---
title: "generic-pae nic-usb modules"
date: 2010-07-13
forum: Server Platforms
---

### Post by fuzzyworbles on 2010-07-13
I'm using the minimal ubuntu install as a virtual machine using the linux-virtual meta-package. This uses the generic-pae kernel, for which I am lacking some modules. I need the modules under .../drivers/usb/nic (or is it nic/usb? .. sorry not using linux right now). the usb core module(s) are present, but i can't seem to figure out how to get usb nics. i tried compiling the needed modules from source, but without any luck (used [http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html))

I've found the nic-usb-modules-generic-pae-...-di package, but it's a "debian-installer" package, which i don't know the first thing about. 

should i just ditch generic-pae, or is there a way to add modules that are otherwise available with plain vanilla? 

thanks

---

