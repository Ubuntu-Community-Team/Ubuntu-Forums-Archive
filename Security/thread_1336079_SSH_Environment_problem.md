---
title: "SSH Environment problem"
date: 2009-11-24
forum: Security
---

### Post by Sirhc64 on 2009-11-24
Good day to all.

I have a small problem. I have set up a laptop(using Ubuntu 8.04) and a workstation(using Ubuntu 9.10) to use ssh without a password, which works fine. I have the same user on both machines with the same user id & group id. I have made an environment file with printenv on the laptop which is in the ~/.ssh of both machines. The problem I am having is that when I lock in from the laptop to the workstation with ssh the environment is not set correctly.
I have a directory on the laptop that I mount with nfs on the workstation so that the path is the same as on the laptop.
My /etc/exports file on the laptop looks like this
> /home/madeleine/OpenFOAM 172.16.1.0/255.255.255.0(rw,no_root_squash,async,subtree_check,anonuid=1002,anongid=100)
and on the workstation I mount the directory as follows
> 172.16.1.108:/home/madeleine/OpenFOAM /home/madeleine/OpenFOAM nfs rsize=8192,wsize=8192  0 0
I would like to know what am I not doing, or doing wrong.

Thanks in advance.

---

### Post by Lars Noodén on 2009-11-24
If the server is set to allow PermitUserEnvironment for the group that user is in, then one of the ways you can set the environment variables is in 

~/.ssh/environment

Or maybe you can have the rc script set them.  It should get run on successful login.

~/.ssh/rc

---

