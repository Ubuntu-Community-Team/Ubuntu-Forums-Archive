---
title: "Is there such a thing as Ubuntu containers?"
date: 2021-04-01
forum: Ubuntu, Linux and OS Chat
---

### Post by salamilimos on 2021-04-01
In PlayOnLinux, it's possible to create Windows containers with different versions of Windows on them, like Windows 3.1 for example and use old software that otherwise isn't installable on newer versions of Windows. PlayOnLinux makes making these containers easy.

It would be cool if this were possible with Ubuntu versions as well, each Ubuntu container with their own Ubuntu version, libraries and repos.

The reason I'm asking this is because my printer doesn't work anymore with Ubuntu, it used to work on 18.04, but not on 20.04, the driver's dependancies and requirements cannot be met with 20.04 and the driver is 32-bit only, so my solution is to use Virtualbox with 18.04 to print with my printer. So it would be cool if there could be Ubuntu containers similar to PlayOnLinux's Windows containers to use old Ubuntu drivers with that otherwise wouldn't work on newer Ubuntu versions.

---

### Post by grahammechanical on 2021-04-01
Try internet searching for Ubuntu LXD. You will find stuff like this

[https://ubuntu.com/blog/lxd-in-4-easy-steps](https://ubuntu.com/blog/lxd-in-4-easy-steps)

[https://linuxcontainers.org/lxd/introduction/](https://linuxcontainers.org/lxd/introduction/)

[https://linuxcontainers.org/lxd/getting-started-cli/](https://linuxcontainers.org/lxd/getting-started-cli/)

And away you go.

Regards

---

### Post by TheFu on 2021-04-01
PlayOnLinux isn't a container with all the security that Linux containers have.  It is just an environment for Windows.  I think the competing products call these different environments "bottles", to go with the whole "WINE" idea.

Linux Containers come in all sorts of types, but the basic underlying capabilities are built into the Linux Kernel using cgroup namespaces and have been since around 2005-ish.  Different names you may have heard are docker, rkt, Podman, runC, containerd, lxd, lxc, and about 20 others.  All of those work on Ubuntu, so it comes down to whether their usual deployments are secure enough for your needs or if you just want convenience with pre-built containers (cough ... docker) provided by unknown sources.

For running 18.04, lxd should work fine, but as kernels move forward, Linux Containers (they share the hostOS kernel) will likely have issues with kernel drivers. Keep that VM around - though you might want to pick a different hypervisor ... or not.  Linux Containers bring restrictions for access to some hardware, so not everything will work under a container environment.  My printers and scanners are all supported, so I haven't needed to fight the battle you are fighting.  I'm careful about selecting external hardware after about a decade of feeling burned. 

Linux also has some lite sandbox capabilities that use cgroups, just not as strict as a full Linux Container.  These include flatpaks, snap packages, and some general solutions like **firejail** and **bubblewrap**. Google has a version of this too.  These are handy when you don't want to build a full container, but just need 1 program to be restricted.  I use firejail with Firefox and Thunderbird every day, all day.

Each has a place in your security and convenience arsenal.

LXD is pushed from Canonical. It can be a nice setup, provided you don't need to go too far back in history.  When that happens, you'll probably need to switch to using a virtual machine running under a hypervisor like KVM or Xen.  It should be possible to run Win 3.1 under a hypervisor, but I'll admit, I've never tried.  Remembering what hardware is supported and how to configure the autoexec.bat/config.sys files aren't high on my list.  I bet OS/2 would fly on modern hardware.  I do have WinXP and Win7 VMs for very specific purposes. They are not allowed on the network for security reasons, except to a very tiny number of specific locations controlled by network firewalls.

I only have a few LXD containers. These are single purpose and do a fine job for what they are.  I've read that running a VPN server inside lxd has challenges due to the networking complexities, but I know running DNS and a Pi-Hole is fairly trivial.  Running web servers would be easy too.  My main complaint about LXD are 2 items:
[LIST]
[*]lxd is only released as a snap package, which means if you won't want snaps on your system, but need lxd, then adding the snap crap is mandatory to have a current release of lxd.
[*]lxd nearly demands that we use ZFS. My attempts to use LVM+ext4 have all failed.  So what I have is LVM-->ext4-->zfs block file
[/LIST]
LXD feels about halfway between running a hypervisor and using something like Docker

BTW, lxd is available for other distros, so it isn't just an Ubuntu Container.  I think the enterprise Canonical container offer uses juju - and I'd guess that is a container manager with integration metadata so hook ups for the web-app to the DBMS running either on the same or different hardware is possible through a drag-n-drop interface. That's all my guess. I've seen a few juju demos, but decided all that "magic" was frail and could easily break, so it was an "avoid" in my book.  If I don't have a full understanding of the infrastructure and how communications occur, then I can't fix them when something breaks.

---

### Post by CatKiller on 2021-04-01
FWIW, driverless printing is a thing now. Even though your printer manufacturer hasn't kept their stuff up to date, you might not actually need it.

---

