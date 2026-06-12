---
title: "Unable to select server kernel with preseed"
date: 2010-01-06
forum: Server Platforms
---

### Post by Xhosa on 2010-01-06
I'm currently trying to use preseed to build an ubuntu server box over the network.  I'm using the netboot.tar.gz from the karmic main mirror.  By default it installs the standard kernel (linux-2.6.31-16-generic), and I want to use the server kernel (the metapackage linux-server which should install linux-image-2.6.31-16-server).

I'm using a minimal build:

```
tasksel tasksel/first multiselect minimal
```

As far as I can see all the other preseed settings are close to defaults.

I've tried setting both of the following lines (separately and together) with no effect:

```
d-i base-installer/kernel/image string linux-server
d-i base-installer/kernel/override-image string linux-server
```

Once the machine is built, if I run:

```
debconf-get-selections --installer
```

It contains:

```

# Kernel to install:
# Choices: linux-386,linux-generic,linux-generic-pae,linux-virtual,linux-image-386,linux-image-generic,linux-image-generic-pae,linux-image-virtual,linux-image-2.6.31-16-virtual,linux-image-2.6.31-16-generic-pae,linux-image-2.6.31-16-generic,linux-image-2.6.31-16-386,linux-image-2.6.31-15-virtual,linux-image-2.6.31-15-generic-pae,linux-image-2.6.31-15-generic,linux-image-2.6.31-15-386,linux-image-2.6.31-14-virtual,linux-image-2.6.31-14-generic-pae,linux-image-2.6.31-14-generic,linux-image-2.6.31-14-386, none
bootstrap-base  base-installer/kernel/image     select  linux-generic
d-i     base-installer/kernel/image     select  linux-generic

```

Which appears to not list any *-server kernels.

Any ideas why this is happening?

---

### Post by craigp84 on 2010-01-06
> d-i base-installer/kernel/override-image string linux-server

You've done it right. That's how to do it. Or at least it was how to do it, maybe it's changed with the latest release?

The best i can come up with is the apt-sources of the installation environment are somehow configured in such a way that it can't see the linux-server package.

Not sure how that could be because surely it's just pointing at a mirror of the complete ubuntu repos over the 'net.

Does the mirror you're using definately contain the linux-server package? What about the packages.gz file on the mirror?

Might be worthwhile, during the installation to drop into a shell and explore what APT thinks is visible?

```
apt-cache search linux-server
```

---

### Post by Xhosa on 2010-01-07
I've grabbed a copy of the 9.10 server install CD and had a look in the preseed folder.

It appears that ubuntu-server.seed has:

```

# Always install the PAE kernel.
d-i	base-installer/kernel/override-image	string linux-generic-pae

```

So it does look like this has changed from being linux-server

---

### Post by craigp84 on 2010-01-07
Fair enough :-) awful lot of changes catching everyone out with 9.10 (I'm looking at you grub2).

I'll need dig up the changelogs and see what else has changed that's potentially a biter of a problem.

---

