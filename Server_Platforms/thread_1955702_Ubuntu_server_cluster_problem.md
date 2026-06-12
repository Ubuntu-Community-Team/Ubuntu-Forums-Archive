---
title: "Ubuntu server cluster problem"
date: 2012-04-10
forum: Server Platforms
---

### Post by bchaffin72 on 2012-04-10
I have built a two node cluster using Ubuntu server 11.04 and MPICH2. I set up a common directory via NFS and passwordless SSH logins.

According to all tests and mpdtrace output, the ring is fully functional and all nodes are communicating.

When attempting to run mpi programs using mpiexec or mpirun, I get this:

rank 1 in job 2  *hostname*_42982   caused collective abort of all ranks
  exit status of rank 1: killed by signal 4 

If I run the programs without mpi, they work, but only on the main node.

something like mpiexec -n 2 /bin/hostname runs the hostname on both nodes, so  I know they are both active and communicating.

Has anyone else running clusters encountered this?

---

