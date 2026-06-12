---
title: "suggestions in replacing OpenSolaris"
date: 2010-09-04
forum: The Cafe
---

### Post by jdrodrig on 2010-09-04
Hi Guys,

Just curious if you would have any suggestions for replacing OpenSolaris in my home-server. I have been using it for six months now, with almost uninterrupted online-ready (thanks to an UPS too) and have loved the lack of problems but mostly, the flexibility of ZFS filesystem and zfs disk pools. 

Do you know of suitable distribution or OS that would have similar ZFS type of characteristics?

---

### Post by inobe on 2010-09-04
any linux with zfs-fuse

[https://build.opensuse.org/package/show?package=zfs-fuse&project=filesystems](https://build.opensuse.org/package/show?package=zfs-fuse&project=filesystems)

the perfect server [http://www.howtoforge.com/perfect-server-opensuse-11.1](http://www.howtoforge.com/perfect-server-opensuse-11.1)

list of others at bottom page

---

### Post by Naiki Muliaina on 2010-09-04
Nexenta are making a follow up to Open Solaris too.

[http://www.illumos.org/](http://www.illumos.org/)

---

### Post by Majorix on 2010-09-04
> **Naiki Muliaina said:**
> Nexenta are making a follow up to Open Solaris too.

[http://www.illumos.org/](http://www.illumos.org/)

They don't have any updates in weeks and not even a development release to test out. How exciting. No offense but I don't buy that.

@OP: You might want to have a look at FreeBSD which in my opinion makes a good server OS. I don't think it supports ZFS, but still it is worth considering.

---

### Post by Naiki Muliaina on 2010-09-04
Websites been built up since last week. Wether or not they announce it on the news page, they have definitely been setting up.

---

### Post by Majorix on 2010-09-04
Don't get me wrong, I certainly hope that they come up with a usable OS from the remainder of OpenSolaris. It is only that I feel a letdown having been checking their page from time to time and seeing no updates.

---

### Post by toupeiro on 2010-09-04
It's sad to see this project go away.  I don't see BSD as a real "replacement" to OpenSolaris.  It was really an alternative UNIX in the philosophies behind it.  I don't really know of a true-form replacement of OpenSolaris, because I don't know what this means to the forks out there like Nexenta and others. I really don't know many other variants of SYSV UNIX out there that are free.

That being said, there is supposed to be an Indian company who has successfully ported ZFS to linux without the use of fuse.  No idea on when this may actually see mainstream daylight.

---

### Post by jdrodrig on 2010-09-05
Thanks guys; this has been useful.

Honestly I still have a tough time accepting the fact that Oracle dropped OpenSolaris's opensourceness... what does that mean? that any advances made by the community built on the trust of opensourceness down the road, became Oracle property now?

I came to OpenSolaris also because, Sun's Fortran Compilers' tools (eg Dtrace, race condition detection) worked only under sun's OS (at leat that was my understanding).

I wonder if other distros with the same kernel would also be suitable for Sun's compilers debugging tools.

ZFS was an extra, but once I got used to it, I have become a fan of its ability to pool different hardware and the power of zfs snapshots. I wonder if ports of zfs would be ready to be put in a "production" environment; do you think that is the case?

---

### Post by Bachstelze on 2010-09-06
> **Majorix said:**
> 
I don't think it supports ZFS,

It does.

---

### Post by slackthumbz on 2010-09-06
Debian.

---

### Post by Naiki Muliaina on 2010-09-06
> **slackthumbz said:**
> Debian.

explain please :)

---

### Post by DemonBob on 2010-09-06
FreeBSD. They have ZFS support, and I have used it on servers for years, since 6.0-release. I love it.

---

### Post by t0p on 2010-09-06
FreeBSD certainly appears to be a popular choice: google **bsd server** and see how many hits talk about FreeBSD.

But as an Ubuntu user on a Ubuntu enthusiast's site: why not try the Ubuntu Server Edition.  I've never used it myself, but the brand brreds confidence... in me, anyway.

---

### Post by Sporkman on 2010-09-06
Ubuntu Server is fast & rock solid.

---

### Post by kaldor on 2010-09-06
I use Ubuntu Server on an ancient PC I use for storage/backups. It's flawless for what I need.

If you want something more like OpenSolaris, try BeleniX or Nexenta? They're notable projects.

---

### Post by Glenn Jones on 2010-09-06
Dragonfly bsd looks good. I've heard that the Hammer file system is very impressive and better than zfs

---

### Post by neu5eeCh on 2010-09-06
> **jdrodrig said:**
> Hi Guys,

Just curious if you would have any suggestions for replacing OpenSolaris in my home-server.

I don't get it? Why switch? If it's been working great for six months, then it will work great for *another* six. By that time, maybe IllumOS will be a contender. If not, then keep using OpenSolaris. Indefinitely. It's not like you're running a mission critical server for God Inc..

---

### Post by Dustin2128 on 2010-09-06
I hear the BSDs make for solid server OSes. As for linux, I'd recommend debian or slackware.

---

### Post by MasterNetra on 2010-09-06
Storm OS uses ZFS. Haven't tried it personally though.
[http://www.stormos.org/](http://www.stormos.org/)

---

### Post by timvalen on 2010-09-09
Wish I could have replied to your post sooner. I think the best answer for you is BeleniX. BeleniX is an OpenSolaris Distribution. Only problem is if you are use to GNOME, BeleniX comes with KDE or Xfce. However I do believe GNOME will be available before to long.

[http://www.belenix.org/](http://www.belenix.org/)

[http://distrowatch.com/table.php?distribution=BeleniX](http://distrowatch.com/table.php?distribution=BeleniX)

Hope this helps, Tim...

---

### Post by 98cwitr on 2010-09-09
I has Ubuntu running as my media server on an old PC for a while...it was great. What are your requirements?

---

### Post by samalex on 2010-09-09
> **Sporkman said:**
> Ubuntu Server is fast & rock solid.

I was about to post the same thing. I've ran Ubuntu Server on my home server for about 5 years now and works quite well.  I haven't used Solaris since college 12 years ago, but what does it offer that Ubuntu Server couldn't?

---

### Post by MattBD on 2010-09-09
I'd go for one of the BSD's - most likely FreeBSD, since that offers ZFS support, along with the excellent Ports system. I've been itching to try it for ages, since it doesn't work too well in Virtualbox.

That said, the other BSD's are good too. OpenBSD has a great reputation for being secure, while NetBSD is renowned for its clean code base.

You might want to consider FreeNAS, which is a FreeBSD-based OS for network-attached storage devices, and comes with all sorts of goodies such as a BitTorrent client and UPnP server, making it ideal for home use.

---

