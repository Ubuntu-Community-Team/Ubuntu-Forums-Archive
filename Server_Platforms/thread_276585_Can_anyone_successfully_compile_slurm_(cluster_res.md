---
title: "Can anyone successfully compile slurm (cluster resource manager)"
date: 2006-10-13
forum: Server Platforms
---

### Post by benhall on 2006-10-13
I've been interested in learning how to build a simple cluster to run simulations on, and I've been investigating different software combinations I might want to use. One resource manager I've been looking at is slurm ([http://www.llnl.gov/linux/slurm/)](http://www.llnl.gov/linux/slurm/)), which has been mentioned in the clusters pages on the wiki.
Has anybody been able to successfully compile slurm? I can run "./configure", "make", and "make install" without errors, but my headnode cannot connect to the others when I run "slurmctrld -D -vvvvvv", giving the error message
> slurmctld: error: agent/send_recv_msg: abbondanza: Unspecified error
"make check" fails at the step below
> 
allocate-tst.c: In function ‘main’:
allocate-tst.c:50: error: ‘resource_allocation_and_run_response_msg_t’ undeclared (first use in this function)
allocate-tst.c:50: error: (Each undeclared identifier is reported only once
allocate-tst.c:50: error: for each function it appears in.)
allocate-tst.c:50: error: ‘run_resp_msg’ undeclared (first use in this function)allocate-tst.c:70: warning: implicit declaration of function ‘slurm_allocate_resources_and_run’
allocate-tst.c:75: warning: implicit declaration of function ‘slurm_free_resource_allocation_and_run_response_msg’

I've installed authd and munge (as well as their dependencies) on the nodes, as well as lam. Are there any other programs that it needs to run, or is it more likely to be related to my server configuration?

Many thanks in advance

---

### Post by moejette on 2006-11-07
> **benhall said:**
> I've been interested in learning how to build a simple cluster to run simulations on, and I've been investigating different software combinations I might want to use. One resource manager I've been looking at is slurm ([http://www.llnl.gov/linux/slurm/)](http://www.llnl.gov/linux/slurm/)), which has been mentioned in the clusters pages on the wiki.
Has anybody been able to successfully compile slurm? I can run "./configure", "make", and "make install" without errors, but my headnode cannot connect to the others when I run "slurmctrld -D -vvvvvv", giving the error message

"make check" fails at the step below

I've installed authd and munge (as well as their dependencies) on the nodes, as well as lam. Are there any other programs that it needs to run, or is it more likely to be related to my server configuration?

Many thanks in advance

Several of us do run slurm with ubuntu for development and testing.
"make check" really can't do much without the deamons running, so I've
removed most of the tests altogether. 
slurmctld needs to be able to communicate with the slurmd daemons running 
on the compute nodes of the cluster. Judging from your message, that 
didn't happen. I'd suggest that you try again with slurmctld and slurmd 
running. You should also review the "quick start admin guide" at
[http://www.llnl.gov/linux/slurm/quickstart_admin.html](http://www.llnl.gov/linux/slurm/quickstart_admin.html)
The "troubleshooting guide" at
[http://www.llnl.gov/linux/slurm/troubleshoot.html](http://www.llnl.gov/linux/slurm/troubleshoot.html)
For more help contact [email]slurm-dev@lists.llnl.gov[/email]

---

