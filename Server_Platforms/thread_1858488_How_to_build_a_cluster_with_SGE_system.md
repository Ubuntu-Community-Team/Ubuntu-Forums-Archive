---
title: "How to build a cluster with SGE system"
date: 2011-10-12
forum: Server Platforms
---

### Post by webappl on 2011-10-12
Hi everyone,

I have some questions about building a linux cluster that need your kind help.

I would like to build a small cluster with several Ubuntu server  machines for running MPI programs. Because a number of users are going  to share this cluster, I am planning to install Sun Grid Engine (SGE)  system to manage the computing resources and jobs.

The SGE installation guide says "Ensure that all users of the Grid  Engine system have the same user names on all submit and execution  hosts". It seems to me that I have to manually set up the same user  accounts on all cluster nodes. For a small cluster with a few machines  and only a handful of users, this is fine. However, I'm curious that  while there are tens of hundreds of nodes and/or many many users on the  cluster, what is the best way to mange the user accounts on the cluster?

Secondly, job submit node(s) and computing node(s) may not be the same  machine. This raises a question about how to share files on all nodes.  Is it necessary to let the user home directories be shared/mounted by  all cluster nodes via a service like NFS? By NFS file share, the user  programs and data are available on all cluster nodes. This will be  convenient. However, it also entails significant NFS traffic. The I/O  speed of the shared disk is critical for the performance of the entire  cluster. I'm not convinced that NFS file share is a good way for a large  cluster with many concurrent running jobs. I am not quite following how  SGE system works around this file share issue. Any correction of my  thoughts and suggestion about this problem would be appreciated.

Thanks in advance.

Alex

---

