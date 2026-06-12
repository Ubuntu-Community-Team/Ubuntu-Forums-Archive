---
title: "Sun Grid Engine - ifort: Command not found"
date: 2010-03-19
forum: Server Platforms
---

### Post by coenvh on 2010-03-19
Dear all,
 
I am using Sun Grid Engine to distribute calculations accross a cluster. I am running Ubuntu 9.10 64 bit on each node. I have a problem related to setting the environmental variables for the Intel Fortran compiler in such a way that SGE works correctly. Currently, I have set the PATH for intel fortran in /etc/environment. 
 
When running a program locally on a cluster node without SGE, there is no problem
(ie. "*ifort test.f90"* works). Hence, at least locally the PATH is correctly set.
 
However, when I submit the same job to the same cluster node using SGE, something goes wrong:
 
*qsub -q node3.q -cwd -b y ifort test.f90*
 
This gives an error: 
 
*ifort: Command not found.*
 
Apparently, when submitting through SGE the PATH is not being used. When I submit the same job using *gfortran* everything works fine. 
 
Can you give me advise on how to set the environmental variables in such a way that SGE can find it. For some reason it *can* find gfortran after all..
 
Thanks in advance!

---

