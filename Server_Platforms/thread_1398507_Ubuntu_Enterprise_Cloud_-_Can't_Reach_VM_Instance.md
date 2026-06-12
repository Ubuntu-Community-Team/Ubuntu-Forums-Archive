---
title: "Ubuntu Enterprise Cloud - Can't Reach VM Instance"
date: 2010-02-04
forum: Server Platforms
---

### Post by ecowden on 2010-02-04
I've been trying to get a few servers up with Ubuntu Enterprise Cloud using the instructions at:

[https://help.ubuntu.com/community/UEC/CDInstall]("https://help.ubuntu.com/community/UEC/CDInstall")

I have gotten up to step 7.5.  I've successfully installed the cluster controller and the node controller, set up credentials, grabbed images and started an instance.  Executing euca-describe-instances yields:

[INDENT]RESERVATION     r-2C4C056E      admin   default
INSTANCE        i-3AE70790      emi-DDB21063    10.0.7.100      172.19.1.2     running  mykey   0       c1.medium       2010-02-04T19:50:30.564Z        cluster1        eki-F3CB10DB    eri-0856114F[/INDENT]

The cluster controller is at 10.0.7.0 and the node controller is at 10.0.7.1.  Both are reachable (via ping and SSH).  The instance seems to be at 10.0.7.100, yet I can't SSH to (or ping) it from either the cluster controller or any other machine on the network.  (And yes: I've run "euca-authorize default -P tcp -p 22 -s 0.0.0.0/0" from step 7.2 to ensure that the port should be open.)

euca-describe-addresses gives:

[INDENT]ADDRESS 10.0.7.100      i-3AE70790 (eucalyptus)
ADDRESS 10.0.7.101      nobody
...[/INDENT]

So it seems to be running exactly where one would expect it.

What do I need to do to make the instance reachable?

---

### Post by particle010 on 2010-03-17
Have you found a solution for this? I am having the same issue, except I can ping but can't ssh.

---

### Post by chamindaindika on 2011-05-27
> **particle010 said:**
> Have you found a solution for this? I am having the same issue, except I can ping but can't ssh.

I'm also struggling with the same issue. Still I couldn't even ping to any of these public/private IP Addresses of the VM. Can you please tell me what I should do for at least to ping to VM. Then afterward I can try the ssh thing. Please help me..........

---

