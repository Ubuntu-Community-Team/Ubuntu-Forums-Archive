---
title: "Problem with beowulf cluster"
date: 2010-01-22
forum: Server Platforms
---

### Post by abraxas334 on 2010-01-22
I have a small cluster consisting of one head node and 5 other nodes.

Everything has been working fine until recently. When i try to submit a job using qsub from my home/USER directory it won't work.
I get this send to /var/mail/user:
PBS Job Id: 5655.clustname.domain
Job Name:   run.sh
Aborted by PBS Server
Job cannot be executed
See job standard error file
and something about there is no home directory.

i can ping the individual nodes, but when i try and ssh into one node i get this error:

```
Could not chdir to home directory /home/mey: No such file or directory
/usr/X11R6/bin/xauth:  error in locking authority file /home/USER/.Xauthority
init.c(375):ERROR:50: Cannot open file '' for 'append'
-bash: cd: /home/USER: No such file or directory
cannot cd to home directory /home/USER

```

obviously my home directory is not mounted or something like that. I checked at a different cluster where i have access to I can ssh into the nodes and then access my home directory files without a problem.
I haven't changed any settings as far as I am aware of on the cluster. So I am not sure how this could have happened. 
I also need to know how to resolve this problem.

thanks

---

### Post by btmiller on 2010-01-25
How are home directories mounted onthe systems? Does each machine have a separate disk partition for /home, or is the home area shared via NFS (as is common with Beowulfs)? If it's shared via NFS, have you checked that the NFS server is working correctly?

---

### Post by abraxas334 on 2010-01-25
I believe it is shared via NFS.

> have you checked that the NFS server is working correctly? 
As our system admin has left and I am now left in charge of this cluster and I don't really know what I am doing I must admit, that i don't even know how to check if the nfs server is working.

---

