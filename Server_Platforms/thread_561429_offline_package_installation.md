---
title: "offline package installation"
date: 2007-09-27
forum: Server Platforms
---

### Post by hpdv9500 on 2007-09-27
hi!

I have a machine on an isolated network running ubuntu server.
i need to install updates and firewall / security packages. As I said the machine is on an isolated test network, hence no connection to the internet is possible even once. However, I have another machine and can download and install packages by copying them on a pendrive or something. I searched quite a lot and found apt-get command options which allow the user to create a list of packages to install which can be copied elsewhere and download them on that machine. That too won't work coz I can't connect to the net even once.

Is there any way I can download and install updates/packages along with dependencies on another machine (unfortunately running windows, all college machines) then transfer them to the linux machine and install them there?

Thanks for reading. Please help/advice with whatever you know/have to say.

Thanks in advance.

---

### Post by aldeby on 2007-09-27
well you can always download the packages you need via Firefox from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") where you can also get tips about their dependencies.
Once you have brought those .deb packages to your server simply go with the terminal into the folder where packages are (e.g typing *cd /media/disk* if your pendrive is mounted in /media/disk) and type
```
sudo dpkg -i *
``` (where * can also be the name of the main package and followed by those of its dependencies)
and you have successfully installed/upgraded!!
Have a happy ubuntu!

PS: also ```
man dpkg
``` will give you a hint about the many other switches dpkg supports to manipulate .deb packages

---

### Post by HermanAB on 2007-09-28
Uhmm, wait - if it is isolated, why bother with updates?  Wait 6 months or a year and install the next release.  In fact, there is probably no reason to do that even - leave well alone is a perfectly good strategy for a standalone machine.

Cheers,

Herman

---

