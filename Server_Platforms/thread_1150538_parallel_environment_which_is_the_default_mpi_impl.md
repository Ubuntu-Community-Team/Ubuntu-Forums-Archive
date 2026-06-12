---
title: "parallel environment: which is the default mpi implementation"
date: 2009-05-06
forum: Server Platforms
---

### Post by Claus7 on 2009-05-06
Hello,

I would like to ask if anyone knows how someone can find out which is the default parallel environment in a server. 

For example there are:
lampi
openmpi
mpich

During compilation of programs I can see in the log files that I have the mpicc library making the links and the like. Yet, this does not indicate which parallel environment I'm using for such a compilation.

The command output of:
mpicc -showme

is:
gcc -I/opt/openmpi/include -pthread -L/opt/openmpi/lib -lmpi -lopen-rte -lopen-pal -lrt -ldl -Wl,--export-dynamic -lnsl -lutil -lm -ldl

Does this mean that I'm using openmpi for mpi implementation?

Thank you,
Regards!

---

### Post by cholericfun on 2009-05-06
sounds plausible,

is there a difference from the programers perspective?
(with mpi standards)

---

