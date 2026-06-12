---
title: "Fedora considers moving all binaries to /usr/bin."
date: 2011-11-02
forum: The Cafe
---

### Post by xang on 2011-11-02
Interesting concept with /usr being conceptually shared between multiple systems/VMs. Also proposed is the elimination of the distinction between /usr/bin /usr/sbin and /bin /sbin.

Original article:

[http://www.h-online.com/open/news/item/Fedora-considers-moving-all-binaries-to-usr-bin-1369642.html](http://www.h-online.com/open/news/item/Fedora-considers-moving-all-binaries-to-usr-bin-1369642.html)

---

### Post by 1clue on 2011-11-02
My first response was "Hell no!" but now that I think about it, permissions and/or access control lists could handle every security concern if they take the time to get it right.

The only real concern I have at this point is that my usual installation has a relatively microscopic / partition and I mount everything else as a separate filesystem.  I would have to think that through for awhile.

---

### Post by crdlb on 2011-11-02
> **1clue said:**
> 
The only real concern I have at this point is that my usual installation has a relatively microscopic / partition and I mount everything else as a separate filesystem.  I would have to think that through for awhile.

So you let the initramfs mount /usr.

---

### Post by juancarlospaco on 2011-11-02
I think Debian its planning a /run on future...

---

### Post by kvvv on 2011-11-02
I like it. Having /usr/bin and /bin can indeed be confusing, and seems redundant especially for newbs like me.

Another thing I wonder about is the difference between /usr/local and /opt. From what I have seen they are both used to store system wide programs that are not inherently part of the distros package manager.

---

### Post by kk0sse54 on 2011-11-02
> I think Debian its planning a /run on future...

Several distro already have since systemd is using it and udev switched to using it by default too

> **kvvv said:**
> I like it. Having /usr/bin and /bin can indeed be confusing, and seems redundant especially for newbs like me.
/bin is traditionally used for critical binaries needed for booting such as 'init' thus allowing /usr to be on a seperate partition that's mounted after root.

> Another thing I wonder about is the difference between /usr/local and /opt. From what I have seen they are both used to store system wide programs that are not inherently part of the distros package manager.

/opt is generally for additional packages outside your package manager i.e. proprietary binary applications. /usr/local is for local data and is usually for programs you've compiled yourself through a simple 'make install'

---

### Post by Lars Noodén on 2011-11-02
> **kvvv said:**
> I like it. Having /usr/bin and /bin can indeed be confusing, and seems redundant especially for newbs like me.

You can find the official descriptions in [hier](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html).  When working with servers or embedded devices it is often useful that /bin and /usr/bin are separate.

It's an interesting goal to be able to mount the partition read-only but it needs more thinking through.  How are they going to get these changes into the [Linux standard base](http://www.linuxfoundation.org/collaborate/workgroups/lsb) first?  Or will they go against the standard?

---

### Post by crdlb on 2011-11-02
> **Lars Noodén said:**
> You can find the official descriptions in [hier](http://manpages.ubuntu.com/manpages/oneiric/en/man7/hier.7.html).  When working with servers or embedded devices it is often useful that /bin and /usr/bin are separate.
Why is it useful? Can an initramfs not be used for the same purpose?
> It's an interesting goal to be able to mount the partition read-only but it needs more thinking through.  How are they going to get these changes into the [Linux standard base](http://www.linuxfoundation.org/collaborate/workgroups/lsb) first?  Or will they go against the standard?

The FHS explicitly allows the toplevel directories to be symlinks, so I don't think there is a problem here.

---

### Post by 1clue on 2011-11-03
> **crdlb said:**
> Why is it useful? Can an initramfs not be used for the same purpose?


The FHS explicitly allows the toplevel directories to be symlinks, so I don't think there is a problem here.

FWIW I don't think it's useful anymore.

It used to be that /sbin, /usr/sbin, /bin and /usr/bin all had distinct purposes.  It made sense back then (I was there) but not so much now.  Over the years, distros I've had exposure to seem to bend their ideas of where things should go and the definitions have blurred somewhat.  As "me" I generally want everything to be on the PATH, even if I can't execute it as my regular user.

It used to be that booting off floppies (before CDROM was commonplace) was a huge PITA, and if something went wrong you wanted to rescue the system rather than just pull your junk off and reformat.  Now, you can boot off a rescue CD, pull your data off and start over.  So isolating directories by putting each on a separate partition no longer makes much sense.

I've rescued a couple systems in the last few years, but in every case I thought about it for awhile and then scraped it off and started over with a fresh install.  I just don't trust a system that has broken or been broken into.  It's no longer difficult to install a new system, it's no longer cost prohibitive or time prohibitive, and it's just plain better all around.

The only thing that bugs me is that /usr changes fairly frequently with software updates and such, and I would rather have my / be inviolate and relatively static.  But thinking on it, most of my arguments are "old school" and I would definitely be open to a change.

---

### Post by Lars Noodén on 2011-11-04
The idea behind /bin and /sbin is to have the binaries needed to bring up the system in the same partition as the system (/)

Putting everything into /usr sounds tidy but it means then that essential programs and utilities are no longer available during the initial phases of start up or if mounting goes awry.

It's already possible to mount / read only if there /home and /var and /tmp are separate or at least symlinked to a separate partition.

---

### Post by szymon_g on 2011-11-04
@Lars Nooden
initframs is used for "rescue mode".

---

