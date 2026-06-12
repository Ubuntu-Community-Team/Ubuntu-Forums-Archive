---
title: "ZFS + Linux - Its comming along!"
date: 2011-05-01
forum: The Cafe
---

### Post by sandyd on 2011-05-01
A while ago, the ZFS filesystem was only for Sun's operating system, Open/Solaris. [A linux kernel module port]("http://zfsonlinux.org"), and a [FUSE module for ZFS]("http://zfs-fuse.net") is now available.

ZFS offers several advantages over normal filesystems.

[LIST]
[*]No need for fsck. Filesystem is repaired "on the fly", thus increasing reliability greatly and removing the need to run fsck at startup.
[*]Creating Pools, and then volumes inside the pools (scroll down for explanation)
[*]Compression
[*]Encryption
[*]Relatively fast transfer speeds when using the kernel module (Not FUSE!)
[*]Snapshots
[*]Parallel operations (ZFS will use multiple threads to use full CPU power during filesystem operations)
[*]Dedup (for file storage)
[/LIST]
[B]ZFS Pools & Volumes
[/B]ZFS is based on pools. A pool is created on a partition. Meanwhile, the pool is separated into 'volumes'. Each of these volumes is part of the pool, and shares space with the pool. Limits can be set on the size of the volume, and the space available to the volume can be guaranteed if necessary.

I.E.: volume1 + volume2 + volume3 = pool 

[B][SIZE=2]Current Status[/SIZE]
[/B]The ZFS-FUSE method can quite slow. As seen in the [benchmarks]("http://cdn.sandyd.me/docs/bonnie++/bonnie_zfs_fuse.html"), it lags in some aspects compared to  [JFS]("http://cdn.sandyd.me/docs/bonnie++/bonnie_jfs.html"). However, it is the easiest to setup.

The ZFS-ON-LINUX kernel module is another story. [ZFS-on-linux]("http://cdn.sandyd.me/docs/bonnie++/bonnie_zfs_module.html") is much faster than [JFS]("http://cdn.sandyd.me/docs/bonnie++/bonnie_jfs.html") and [ZFS-FUSE]("http://cdn.sandyd.me/docs/bonnie++/bonnie_zfs_fuse.html"). The main problem is that it does not support PREEMPT kernels yet, due to[ this bug]("https://github.com/behlendorf/zfs/issues/83") (all kernels have voluntary preemption enabled), so it will have to be turned off in order for ZFS to function properly. Additionally, only **[COLOR=#22ccff]0.6.0-rc3[/COLOR]**+ versions.

It does not work with hardened kernels. Works up to 2.6.38 (although it states that its only supported by the developer up to kernel 2.6.36). Kernel 2.6.39 is in the works ([check the commits & bugs currently in github]("https://github.com/behlendorf/zfs/commits/master"))

~I will add more info later + tutorials once I get my Ubuntu VM setup within the next day or two.
Feel free to ask questions, since Im running ZFS for my home directory right now.

p.s. hard drive used was a standard 5400RPM laptop hard drive.

**Links**
[ZFS On Linux]("http://zfsonlinux.org") | [SPL (required by ZFS)]("https://github.com/behlendorf/spl") | [Source Code]("https://github.com/behlendorf/zfs") | [Bugs]("https://github.com/behlendorf/zfs/issues?_pjax=true&state=open") | [Bonnie++]("http://cdn.sandyd.me/docs/bonnie++/bonnie_zfs_module.html")
[ZFS-FUSE]("http://zfs-fuse.net") | [Source Code]("http://zfs-fuse.net/releases") | [Bonnie++]("http://cdn.sandyd.me/docs/bonnie++/bonnie_zfs_fuse.html")

---

### Post by juancarlospaco on 2011-05-01
Btrfs

---

### Post by madjr on 2011-05-01
zfs and btrfs are awesome.

all those features, specially the snapshots are amazing.

anyway when you estimate we will have one of these as default?

---

### Post by sandyd on 2011-05-01
> **madjr said:**
> zfs and btrfs are awesome.

all those features, specially the snapshots are amazing.

anyway when you estimate we will have one of these as default?
Never for ZFS.
Its a licencing issue concerning GPL (3), so it will not be part of the kernel until Oracle changes the licencing.

Btrfs is already in, but still no fsck tool.
Marked as Experimental & as an unstable disk format, which means you need to enable
```

&#9474; Symbol: EXPERIMENTAL [=y]                                                                              &#9474;   
  &#9474; Type  : boolean                                                                                        &#9474;   
  &#9474; Prompt: Prompt for development and/or incomplete code/drivers                                          &#9474;   
  &#9474;   Defined at init/Kconfig:33                                                                           &#9474;  
  &#9474;   Location:                                                                                            &#9474;   
  &#9474;     -> General setup

```In the kernel for btrfs to appear. Results may vary, since I use gentoo with the vanilla kernel.

After you enable EXPERIMENTAL, [check screenshot]

---

### Post by sandyd on 2011-05-01
> **juancarlospaco said:**
> Btrfs
I trust ZFS more, its a more stable disk format (while btrfs is marked as unstable disk format in the kernel). Only the driver isn't fully functional.

---

### Post by juancarlospaco on 2011-05-01
> **sandyd said:**
> its a more stable disk format

 Only the driver isn't fully functional.

No.

Even its on the Official Ubuntu Natty as a possible Filesystem for installation.

---

### Post by sandyd on 2011-05-01
> **juancarlospaco said:**
> No.

Even its on the Official Ubuntu Natty as a possible Filesystem for installation.
its possible, but I still trust that the linux kernel developers listed BTRFS as unstable, and experimental for a reason.

---

### Post by juancarlospaco on 2011-05-01
> **sandyd said:**
> linux kernel developers listed BTRFS as unstable

Not more recently.

---

### Post by sandyd on 2011-05-01
> **juancarlospaco said:**
> Not more recently.
check the attached screenshot above.

thats the linux-2.6.38 kernel, which is the most recent stable kernel. still listed as unstable and experimental. Partly attributed to no fsck.

---

### Post by madjr on 2011-05-02
> **sandyd said:**
> Never for ZFS.
Its a licencing issue concerning GPL (3), so it will not be part of the kernel until Oracle changes the licencing.

Btrfs is already in, but still no fsck tool.
Marked as Experimental & as an unstable disk format, which means you need to enable
```

&#9474; Symbol: EXPERIMENTAL [=y]                                                                              &#9474;   
  &#9474; Type  : boolean                                                                                        &#9474;   
  &#9474; Prompt: Prompt for development and/or incomplete code/drivers                                          &#9474;   
  &#9474;   Defined at init/Kconfig:33                                                                           &#9474;  
  &#9474;   Location:                                                                                            &#9474;   
  &#9474;     -> General setup

```In the kernel for btrfs to appear. Results may vary, since I use gentoo with the vanilla kernel.

After you enable EXPERIMENTAL, [check screenshot]

hm, i know zfs is not part of the kernel... but if the ubuntu guys wanted to make it the default option for next release instead of ext4, they cant ?

also have you tried the snapshots? are they working?

---

### Post by sandyd on 2011-05-02
> **madjr said:**
> hm, i know zfs is not part of the kernel... but if the ubuntu guys wanted to make it the default option for next release instead of ext4, they cant ?

also have you tried the snapshots? are they working?
a) Depends. They wouldn't add it right now due to the preempt bug (as voluntary preemption is enabled by default), but its possible that they can add it to the next ubuntu release. However, I have never seen Ubuntu add 3d-party filesystem drivers that are not included in the kernel. Since filesystems are so important, I do not think that the ZFS driver has neared the stage of maturity & testing needed to be as a kernel module in a distro such as Ubuntu. I believe that they should have a kernel module package for ZFS though. I might introduce one to my ppa after the PREEMPT bug clears up. Its easy to make a package since theirs no external dependencies other than the kernel source code, SPL (solaris porting layer) and ZFS. I would just have to add those to the build-dep, and stick it into launchpad. After I upload my new PgP key that is.

However, most likely, the module will **not** be part of the kernel drivers package, or patched in the kernel itself, but as a seperate package.

b) im running from the snapshots right now. Its fully working, as long as you disable CONFIG_PREEMPT in the kernel (no preemption). See the bug listed in the first post to disable the primarycache.

---

### Post by ssam on 2011-05-02
> **sandyd said:**
> Never for ZFS.
Its a licencing issue concerning GPL (3), so it will not be part of the kernel until Oracle changes the licencing.


it just needs to be reimplemented under a GPL compatible licence. did linux wait for microsoft to GPL FAT?

---

### Post by AnXioZ on 2011-06-02
sandyd how has your experience been so far? Any problems, or annoying quirks? 

I have been using WHS with DE for my home server, and I've been lurking at Ubuntu Server + ZFS as a replacement.

---

