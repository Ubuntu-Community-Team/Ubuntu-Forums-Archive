---
title: "lxc servers down?"
date: 2014-12-07
forum: Virtualisation
---

### Post by krafczyk-matthew on 2014-12-07
Hi,

I'm trying to create an lxc container on my 64 bit ubuntu 14.10 distribution. I want the lxc container for a 32 bit development environment. However I can't proceed with the lxc-create command. It just hangs at "Downloading the image index".

I think this is because currently the linuxcontainers.org website is down.

What I'd like to know is whether there is any alternative to the directions here: [https://help.ubuntu.com/lts/serverguide/lxc.html](https://help.ubuntu.com/lts/serverguide/lxc.html)
Which indicate that I should use -t download, and then specify that I want ubuntu, utopic, and i386.

Thanks for any suggestions.

---

### Post by krafczyk-matthew on 2014-12-08
For people stumbling across this,

It seems another way is detailed by the wine people here:  [http://wiki.winehq.org/WineOn64bit#head-ec78c77745c37a264ed79173d9704efc286514fc](http://wiki.winehq.org/WineOn64bit#head-ec78c77745c37a264ed79173d9704efc286514fc)

Like this you can pass -t ubuntu, and then the options like --bindhome or -a or --release to make sure you get the right version of w/e distro you're interested in. This way, it doesn't seem to download from any of linuxcontainer.org's servers, and you don't have to worry about them being down.

---

