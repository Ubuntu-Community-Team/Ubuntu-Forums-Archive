---
title: "Grid Engine can not display information of excutation hosts"
date: 2010-10-18
forum: Server Platforms
---

### Post by ganyx on 2010-10-18
Hi,

I have installed grid engine at Ubuntu Server 10.10 for our cluster. The frondend and compute nodes has been configured and added to the host list of grid engine.

While using qhost -q at both frondend (pgcluster) and compute node, the same information is given
```

HOSTNAME                ARCH         NCPU  LOAD  MEMTOT  MEMUSE  SWAPTO  SWAPUS
-------------------------------------------------------------------------------
global                  -               -     -       -       -       -       -
computenode01           -               -     -       -       -       -       -
pgcluster               lx26-amd64     24  0.23   31.5G    1.5G   33.9G     0.0

```

Apparently, the compute node is not recognized and can not used by submitting jobs.

Anyone has an idea why there is no available information from the compute node? 

Thanks!
G

---

