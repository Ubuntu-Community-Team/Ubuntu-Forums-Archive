---
title: "ZFS for ubuntu server?"
date: 2012-02-05
forum: Server Platforms
---

### Post by pepsifx357 on 2012-02-05
Hey all,

I'm wanting to install Ubuntu on a ZFS partition.  Is this possible with nothing more than an Ubuntu server disk and an internet connection?

I just found out how ZFS works and it's awesome!  I just figured why not pair the two together to get a great system.

Thanks,

Ben

---

### Post by linuxpyro on 2012-02-05
Due to licensing, ZFS wasn't developed in the mainline Linux kernel tree.  You're not going to get out-of-the-box support for it on an Ubuntu server machine because of this.

However, there was some third-party development on a module to implement ZFS in Linux.  I've never used it, but I found a page about it here:
[http://zfsonlinux.org/]("http://zfsonlinux.org/")

I don't know if that module will let you boot from ZFS, but I'd imagine it would let you set up storage using it.  I can't say how stable it is either, but it looks like it might be fine.  The other option for Linux is to run it using Fuse, which is possible but slow, and so I wouldn't recommend it.  

Also, I know this isn't really what you're asking, but if you're curious you may want to take a look at Solaris, or better yet OpenIndiana (which is an open source fork).  ZFS is native to both of these, although they would require learning a new operating system.

---

### Post by rubylaser on 2012-02-06
> **linuxpyro said:**
> Due to licensing, ZFS wasn't developed in the mainline Linux kernel tree.  You're not going to get out-of-the-box support for it on an Ubuntu server machine because of this.

However, there was some third-party development on a module to implement ZFS in Linux.  I've never used it, but I found a page about it here:
[http://zfsonlinux.org/]("http://zfsonlinux.org/")

I don't know if that module will let you boot from ZFS, but I'd imagine it would let you set up storage using it.  I can't say how stable it is either, but it looks like it might be fine.  The other option for Linux is to run it using Fuse, which is possible but slow, and so I wouldn't recommend it.  

Also, I know this isn't really what you're asking, but if you're curious you may want to take a look at Solaris, or better yet OpenIndiana (which is an open source fork).  ZFS is native to both of these, although they would require learning a new operating system.

ZFSonlinux is actually very usable at this point, but you won't be booting from it at this point.  Personally, I just use Solaris 11 or Openindiana for my servers.  If you go the Solaris route, you'll want to make sure you create your pool with pool version 28, so that it's portable to other systems like zfsonlinux, FreeBSD, Openindiana, or [Nexentastor]("http://www.nexentastor.org/").  Personally, I'd wait to trust my data on zfslinux once they have a stable release, so that this point, I'd look to one of the other options.

If you go the Solaris / Openindiana route, you'll need to be prepared to break out your Google searching skills for a while if you've never used it before, but it's not too hard.  Also installing [napp-it]("http://napp-it.org/") makes it dead simple to manage you array, shares, SMART monitoring, scrubs, etc.

---

### Post by pepsifx357 on 2012-02-06
So for now it would be better to get Solaris or one of the forks?

I imagine that Solaris does just about everything Ubuntu does right?  I haven't really gone through the differences other than Solaris is pretty much unix and has ZFS.

---

### Post by rubylaser on 2012-02-06
> **pepsifx357 said:**
> So for now it would be better to get Solaris or one of the forks?

I imagine that Solaris does just about everything Ubuntu does right?  I haven't really gone through the differences other than Solaris is pretty much unix and has ZFS.

That's what I did.  If you make sure your pool version is 28, it will be very portable and can be easily migrated to zfsonlinux in the future if you choose to.  Also, everything I've read is that zfsonlinux is very stable, so don't let me steer you away from it without doing your own research.  I just won't trust my data to it until it has a newer (supports v28 pools), stable release.

What services do you plan to run on your server?  I run everything I want to on my server, but there would certainly be some things that would be much easier to get working in Ubuntu.

---

### Post by linuxpyro on 2012-02-06
> **pepsifx357 said:**
> So for now it would be better to get Solaris or one of the forks?

I imagine that Solaris does just about everything Ubuntu does right?  I haven't really gone through the differences other than Solaris is pretty much unix and has ZFS.

The userland is different, obviously, but if you're comfortable in Ubuntu you could get used to them.  I'd recommend it if you're just planning on setting up a file server.  They're capable of a lot more, of course like rybylaser said, but for something like a Web/Email server I generally prefer Ubuntu or Debian myself.

[QUOTE=rubylaser]
That's what I did. If you make sure your pool version is 28, it will be very portable and can be easily migrated to zfsonlinux in the future if you choose to. Also, everything I've read is that zfsonlinux is very stable, so don't let me steer you away from it without doing your own research. I just won't trust my data to it until it has a newer (supports v28 pools), stable release.
[/QUOTE]

That's good to know, I'll have to keep an eye on zfsonlinux.

---

### Post by rubylaser on 2012-02-06
Durr, I forgot about Debian kFreeBSD which also supports ZFS.
[32 bit]("http://cdimage.debian.org/debian-cd/6.0.4/kfreebsd-i386/iso-cd/debian-6.0.4-kfreebsd-i386-netinst.iso")
[64 bit]("http://cdimage.debian.org/debian-cd/6.0.4/kfreebsd-amd64/iso-cd/debian-6.0.4-kfreebsd-amd64-netinst.iso")

And, apparently it is possible, although difficult to do an [Ubuntu install on ZFS]("https://github.com/dajhorn/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem").

---

