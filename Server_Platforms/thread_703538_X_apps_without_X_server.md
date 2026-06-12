---
title: "X apps without X server"
date: 2008-02-21
forum: Server Platforms
---

### Post by sigmoid on 2008-02-21
I'm building a thin virtual appliance server (with vmware server) for certain intranet tasks. I'm running an X server on the host system already, so I'd like X apps from the virtual machine to connect to the X server on the host system.
Now this is not the hard part, I've done stuff like this several times before.

However, while not new to Linux, I'm definitely new to Ubuntu, and to me it seems that a single X application (the synaptic package manager) I tried to install wanted to pull in the whole Xorg package complete with a wm (I don't need a wm, I'm running one on my host system already), xcalc, xeyes, all the xwhatevers and xthingies I definitely don't need, not to mention half of the Gnome environment.
Now this is supposed to be a SMALL server. One that doesn't really take up space. I'd like software to pull in the LIBRARIES they're linked to, and not stuff that are SUPPOSED to be necessary. Is there a distinction in the .deb dependency system between the two types of dependency? One would think the first is a "depends", and the second is a "recommends". However, seeing the whopping list of unnecessary stuff aptitude wanted to add, I got a bit lost about this.

Is there a way of doing what I want with Ubuntu, or should I move on to another distro?

---

### Post by HermanAB on 2008-02-21
You are forever going to run into issues like that.

The only solution is to build everything from source yourself.  However, the only practical solution is to fuhgedaboudit and install all the crap, then clean it up a bit later if you really have the time to waste.  With today's umpteen gazillion byte disk drives, this is not really a problem.  

If you are building an embedded system, then you should get a special distro from Montavista for example.

---

### Post by koenn on 2008-02-21
You could check the Depends, Recommends and Suggests of synaptic with
```
apt-cache show synaptic
```
I had a look and don't see any X apps there (some X libs, yes), but I'm using dapper, maybe the package was modified in more recent releases

There is indeed a difference between Depends, Recommends and Suggests (detailled in the Debian packaging guidelines) - It would be highly unusual for any package (other than parts of the X system) to Depend on X, given that you might be useing a remote X server, as you are. 

IIRC, aptitude by default treats Recommends as Dependencies. You can use it with --without-recommends, or just use apt-get.

If your synaptic package has too much GUI that it pulls in, even as 'Recommends', then probably (& IMO) the packagers made an error in judgement or are abusing the Dependency system to manage software delivery in a way that wasn't intended in the design of apt. I'd report it as a bug, then (but check the Depends, Recommends, ...) first.

---

### Post by dca on 2008-02-21
On a Ubuntu 6.06LTS headless server, after install to get VMware running, I think the only thing needed for install was the 'xorg-dev' package (plus whatever it brings along with it)...

---

### Post by sigmoid on 2008-02-21
> **koenn said:**
> IIRC, aptitude by default treats Recommends as Dependencies. You can use it with --without-recommends, or just use apt-get.
Thanks, that was the solution. It was the recommends installed as dependencies that cluttered up the install.

---

