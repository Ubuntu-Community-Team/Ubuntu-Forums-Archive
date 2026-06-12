---
title: "trying to learn how to get out of trouble"
date: 2013-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by breezypt on 2013-04-13
'sudo apt-get update && sudo apt-get install linux-headers-$(uname -r) build-essential'

Is the above command for putting in a fresh kernel? A lot of times I get in trouble with the 
kernel. Number one problem being that I have to rebuild the kernel to put the real nvidia drivers in to get the latest support and functionality

I'm trying to learn some important linux commands and would just like to double check if this is the right terminology to start off with a fresh kernel...

Thanks,

John

---

### Post by cariboo on 2013-04-14
Compiling your own kernel isn't for the faint of heart, I'd advise that if the default kernel for the version you are using doesn't work for you, you may want to try one of the mainline kernels available here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Just download the three packages, plus the *all.deb package for your architecture and once downloaded use:

```
sudo dpkg -i *.deb
```

the above command assumes you don't have any other .deb packages in your download directory.

The mainline builds don't include any of the Ubuntu enhancements that we see in the default kernel builds.

For more info on the mainline kernels have a look at the [wiki]("https://wiki.ubuntu.com/Kernel/MainlineBuilds") page.

---

