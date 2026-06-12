---
title: "dmesg messages like &quot;[272749.305341]  sde:&quot;"
date: 2017-04-05
forum: Server Platforms
---

### Post by pancyber on 2017-04-05
Hello friends,
I have a small home server built out of an old Intel SS4200 upgraded with  an E4700@2.60GHz and 2GB Ram.
A *friend* gave me 4x 4TB WD "Red" EFRX disks which I've put into raid 10 for speed and security, while I keep the ubuntu server installation on a separate 64GB IDE DOM I purchased from AliExpress dirt-cheap.

Everything works great, mdstat, smart, etc say no problem, and a full e2fsck -c -c I've run finished (after 4 days) with absolutely no errors.
```

md0 : active raid10 sdc[1] sdb[0] sdd[2] sde[3]
      7813774336 blocks super 1.2 512K chunks 2 near-copies [4/4] [UUUU]
      bitmap: 1/59 pages [4KB], 65536KB chunk

```

**BUT...**
every 5 minutes I get those strange lines at dmesg and syslog:

```

Apr  5 21:32:56 nas kernel: [272448.939736]  sdd:
Apr  5 21:32:56 nas kernel: [272448.994534]  sde:
Apr  5 21:37:57 nas kernel: [272749.209176]  sdd:
Apr  5 21:37:57 nas kernel: [272749.305341]  sde:
Apr  5 21:43:07 nas kernel: [273059.443956]  sdd:
Apr  5 21:43:07 nas kernel: [273059.539012]  sde:
Apr  5 21:48:17 nas kernel: [273369.879935]  sdd:
Apr  5 21:48:17 nas kernel: [273369.984527]  sde:
Apr  5 21:53:18 nas kernel: [273670.150164]  sdd:
Apr  5 21:53:18 nas kernel: [273670.252729]  sde:
Apr  5 21:58:28 nas kernel: [273980.407587]  sdd:
Apr  5 21:58:28 nas kernel: [273980.509230]  sde:

```
Those are my [2] and [3] members of the raid 10 array...

Does anyone know what are those about and why I don't get any lines like those for my other 2 members?

Many thanks !!!

---

