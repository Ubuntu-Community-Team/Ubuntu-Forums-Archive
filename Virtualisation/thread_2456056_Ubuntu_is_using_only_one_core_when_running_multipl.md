---
title: "Ubuntu is using only one core when running multiple jobs"
date: 2021-01-03
forum: Virtualisation
---

### Post by xrobot2 on 2021-01-03
I created a VM (Ubuntu 20.04) on Win-10 system with Hyper-V and allocated 20 cores (out of 24) to this VM. It worked fine till I ran multiple python jobs in the background. 

on a remote machine, I SSH into this VM and launch the python jobs with a script like this:

#!/bin/bash
python job1.py  > ~/tmp/log.txt 2>&1 &
sleep 3s
python job2.py  > ~/tmp/log.txt 2>&1 &
sleep 3s
......



Then I noticed that only one core (out of 20) is running at 100%, all the rest are idle. 
I ran this same on a native Ubuntu server (also 20.04), it would use all the cores and much faster.  



I am new to Hyper-V and just started to explore Ubuntu VM yesterday, it was pretty smooth other than this problem. I think it should be a typical set-up but did not find many discussions on this issue. I would very much appreciate if any experts here could point out what the problem might be. Thanks!


[PS] In case someone see a similar problem in the future: it turned out to be a CPU affinity problem rather than virtualization problem. I solved it with *taskset *command.

---

### Post by TheFu on 2021-01-03
Not many people here will run hyper-v. May want to ask this question in some ms-windows forums.

May want to dbl check the number of vCPUs in the VM settings too. Generally, more is NOT better, unless they are actually needed. Linux systems don't need a different kernel loaded based on the number of available vCPUs.  I don't know if this is still true, but MSFT installed different kernels based on whether 1 core or more was seen during installation time.  That isn't how Linux works.

Virtualization is about sharing limited resources efficiently.  Just because you CAN do something, doesn't make it a good idea. I can't see many reasons for any Linux desktop to need more than 2 vCPUs.  
Most Linux servers in a home environment would be hard pressed to use more than 2-4 vCPUs.  Geospatial DBMS workloads can definitely use larger numbers of vCPUs, but RAM and disk performance would matter more.  
I self-host a number of Linux servers running all sorts of stuff for a few businesses. Only our shared "communications" server gets 2 vCPUs.  The email gateway runs in a tiny VM - 1 vCPU and 384 MB of RAM with just 8G of storage (using 4.4G).  Linux computers aren't Windows computers.  Most servers do fine with 1 GB of RAM and 1 vGPU.  Just depends on the workload.

These systems are up 24/7 and only rebooted when a new kernel needs it. I refuse to trust the live-patching capability which can allow running kernels to be patched for longer uptimes.  Every few weeks, 30 seconds of scheduled downtime is fine. I actually have 4 hrs scheduled every Saturday morning to patch, but usually don't need any downtime and impacted services might be stopped/restarted taking 10 seconds, if that.
When the VM hosts (Ubuntu Server 16.04 KVM as hypervisor) need to be bounced, that impact all the VMs running and does require about 2 minutes of downtime, if I don't live migrate those running VMs to a different host first.

---

### Post by xrobot2 on 2021-01-04
thanks will post at msdn

---

