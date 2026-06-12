---
title: "kernel flavors for server amd64"
date: 2006-02-07
forum: Server Platforms
---

### Post by eudoxos on 2006-02-07
There are different flavors of kernels precompiled for amd64: generic, k8, xeon, server. I couldn't find any specification which one is optimized for what (neither google, nor ubuntu wiki / launchpad), can someone point me to some specs?

I am running application (terminal) server with 2 Opterons, so I need kernel that is reasonably interactive (preemption), supports 4G RAM and NUMA. Which one to choose? Obviously not xeon, what about the rest? Package descriptions are not very descriptive in this respect.

Thanks for pointers,

Eudoxos

---

### Post by mdr on 2006-02-08
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
has some info 

a specific server kernel hey? - must startx sometime :)

---

### Post by LordHunter317 on 2006-02-08
[QUOTE=eudoxos]I am running application (terminal) server with 2 Opterons, so I need kernel that is reasonably interactive (preemption),[/quote]None of the AMD64 kernels have preemption enabled because it is broken on AMD64.

>  supports 4G RAM and NUMA. Which one to choose? Obviously not xeon, what about the rest? Package descriptions are not very descriptive in this respect.You have a K8, so take the K8 package.

---

