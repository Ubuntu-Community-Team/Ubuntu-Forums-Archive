---
title: "upgrading to server"
date: 2012-12-21
forum: Server Platforms
---

### Post by astarmathsandphysics on 2012-12-21
is it possible to upgrade from ubuntu desktop to server?
Am running 12.04

---

### Post by cwsnyder on 2012-12-21
Short answer, just add the packages, which are available in the repositories.

Longer answer:  Ubuntu server is normally installed without any desktop software and is expected to be administered from another machine.  You certainly can run a desktop while it acts as a server, but it won't be a very efficient desktop or server.

---

### Post by SeijiSensei on 2012-12-21
"Server" is not really all that different from "desktop" except for the lack of a GUI and the fact that most server packages are not installed by default on a standard client.  If you know what services you want to run, you can install them manually on top of your client installation.  

Another option is to install VirtualBox on your desktop, and install the server version into a virtual machine.  If you take this route, follow the instructions for "Debian-based" distributions on [this page]("https://www.virtualbox.org/wiki/Linux_Downloads") to install.

---

### Post by spynappels on 2012-12-22
Just check which version of desktop you are running, if you are running 32bit Desktop, but the machine is capable of 64bit, you'd be safer running 64bit Server, even though this would require a re-install.

If you are on the correct architecture already, you could just remove the desktop (Gnome or KDE etc) packages and install whatever server packages you need which are not already installed, as previously suggested.

---

### Post by tgalati4 on 2012-12-22
The server kernel has some tweaks that are optimized for server workloads.  The desktop kernel is optimized for desktop use.  So depending on what kind of workload you expect, you might be better off doing a fresh install of the server or keep the desktop running and just keep installing services until the machine gets to slow to be useful.

---

### Post by lykwydchykyn on 2012-12-23
> **tgalati4 said:**
> The server kernel has some tweaks that are optimized for server workloads.  The desktop kernel is optimized for desktop use.  So depending on what kind of workload you expect, you might be better off doing a fresh install of the server or keep the desktop running and just keep installing services until the machine gets to slow to be useful.

... or you could just install the server kernel?
```

sudo apt-get install linux-image-server

```

---

### Post by Cheesemill on 2012-12-23
> **tgalati4 said:**
> The server kernel has some tweaks that are optimized for server workloads.  The desktop kernel is optimized for desktop use.
Not true.

This used to be the case but both Server and Desktop have used the same kernel now for the last few releases.

> ... or you could just install the server kernel?
```
sudo apt-get install linux-image-server
```The linux-image-server is just a dummy package that installs the standard linux-image-generic kernel, it only exists for backwards compatibility.
[http://packages.ubuntu.com/quantal/linux-image-server](http://packages.ubuntu.com/quantal/linux-image-server)

---

