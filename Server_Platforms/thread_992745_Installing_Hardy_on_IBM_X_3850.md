---
title: "Installing Hardy on IBM X 3850"
date: 2008-11-25
forum: Server Platforms
---

### Post by raghaven.kumar on 2008-11-25
Hi all,

I am trying to install Ubuntu Hardy on the IBM X 3850 M2.
Its giving kernel not supported.

On googling, i found that i should add **maxcpus=1** to kernel boot line
The server is a quad-core one, so will this option disable that??
and why should i add that?

Will there be any future issues in it?

---

### Post by markharding557 on 2008-11-25
maxcpus specifys the no of cores to use so you have option of 1,2 or4 cores so you can try maxcpus=1or2

---

