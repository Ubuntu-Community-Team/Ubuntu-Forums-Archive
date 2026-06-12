---
title: "Unable to install the build and header files to run VirtualBox Guest Additions"
date: 2008-11-13
forum: Server Platforms
---

### Post by smQQkin on 2008-11-13
Hi,

I having been trying to install VirtualBox Guest Additions 2.0.4. However, when I try to install Guest Additions I get the following error:

**Please install the build and header files for your current Linux Kernel. The current kernal version is 2.6.27-7-server. Problems were found to prevent the Guest Additions from installing. Please correct these problems and try again.**

When I try to install build essentials it says that the files are updated already. I used the following:

sudo apt-get install build-essential

I tried doing sudo apt-get update and then running sudo apt-get install build-essential. But, it still fails.

Anyone have any ideas? :confused:

---

### Post by pressit on 2008-11-30
hey,

check this URL and follow the instruction :

[http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/](http://www.cyberciti.biz/faq/howto-install-kernel-headers-package/)

---

