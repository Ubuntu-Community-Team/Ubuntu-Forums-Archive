---
title: "Maximum # of CPUs? a simple Q for EUCA admins"
date: 2010-05-05
forum: Server Platforms
---

### Post by tarekeldeeb on 2010-05-05
Hello server admins,

I have installed Ubuntu 10.4 server cloud successfully. I have 3 nodes, each has a QuadCore with 4 GB of RAM.

I want to configure a machine size/type (ex c1.xlarge) to have 12 CPU. The free/max always gives 0/0, although my m1.medium (4 CPU) gives 3/3

Can eucalyptus offer CPU+MEM merging into a single VM?

I knew that I configure nodes with MAX_CORES/MAX_MEM, but this exposes more resources to the cloud for extra loading the nodes. I am asking about sharing real CPUs from different nodes into a single VM.

I want to build a monster machine to crunch much data :lolflag:

Thanks in advance,
Tarek

---

### Post by tarekeldeeb on 2010-05-06
To be more clear,

I have 3 nodes each with a quadcore (total = 12 CPU core)

What I can currently do: build 12 virtual machine (VM) each with 1 core

What I want: build 1 VM with 12 CPU. Is this possible?

---

### Post by windependence on 2010-05-06
AFAIK, 

1.Intel x86:
Maximum CPUs: 32 (including logical CPUs)
Maximum memory: 64GB
Maximum filesize: 8TB
Maximum filesystem size (ext3) 16TB
Maximum per-process virtual address space: 4GB


 2.AMD64/EM64T:
Maximum CPUs: 64
Maximum memory: 128GB
Maximum filesize: 8TB
Maximum filesystem size (ext3): 16TB
Maximum per-process virtual address space: N/A


You should be fine.


-Tim

---

