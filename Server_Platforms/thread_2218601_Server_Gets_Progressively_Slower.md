---
title: "Server Gets Progressively Slower"
date: 2014-04-21
forum: Server Platforms
---

### Post by dave-davemackey on 2014-04-21
I have a VPS ("droplet") with DigitalOcean. It has 512 MB RAM and a 20 GB SSD hard drive. The OS is Ubuntu 14.04.

The server runs decently after a fresh boot, but becomes progressively slower over time. Running top dos not seem to be very helpful.

Here is a capture:

```
top - 11:04:57 up 7:59, 1 user, load average: 0.00, 0.03, 0.05
Tasks: 81 total, 1 running, 80 sleeping, 0 stopped, 0 zombie
%Cpu(s): 0.0 us, 0.0 sy, 0.0 ni,100.0 id, 0.0 wa, 0.0 hi, 0.0 si, 0.0 st
KiB Mem: 502968 total, 455096 used, 47872 free, 15144 buffers
KiB Swap: 524284 total, 260 used, 524024 free. 241300 cached Mem

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
1 root 20 0 33588 2804 1408 S 0.0 0.6 0:01.04 init
2 root 20 0 0 0 0 S 0.0 0.0 0:00.00 kthreadd
3 root 20 0 0 0 0 S 0.0 0.0 0:00.36 ksoftirqd/0
5 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/0:0H
6 root 20 0 0 0 0 S 0.0 0.0 0:00.00 kworker/u:0
7 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kworker/u:0H
8 root rt 0 0 0 0 S 0.0 0.0 0:00.00 migration/0
9 root 20 0 0 0 0 S 0.0 0.0 0:00.00 rcu_bh
10 root 20 0 0 0 0 S 0.0 0.0 0:00.88 rcu_sched
11 root rt 0 0 0 0 S 0.0 0.0 0:00.26 watchdog/0
12 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 cpuset
13 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 khelper
14 root 20 0 0 0 0 S 0.0 0.0 0:00.00 kdevtmpfs
15 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 netns
16 root 20 0 0 0 0 S 0.0 0.0 0:00.00 bdi-default
17 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kintegrityd
18 root 0 -20 0 0 0 S 0.0 0.0 0:00.00 kblockd
```

Significant applications installed on the server are: apache, exim, mysql, newrelic, openjdk, php, perl, python.

Any thoughts on what is causing this issue? The sites still run, though sometimes slowly (it is being used as a web server) and SSH is somewhat slow, but not inoperable.

Thanks,
Dave

---

### Post by CharlesA on 2014-04-21
Try running a mtr to the IP of your VPS:

```
mtr ip.goes.right.here
```

Submit a ticket and have them check your host node to see if anyone is abusing it.

---

### Post by dave-davemackey on 2014-04-21
Here are the results of running WinMTR...and I'm submitting a ticket.

```
|------------------------------------------------------------------------------------------|
|                                      WinMTR statistics                                   |
|                       Host              -   %  | Sent | Recv | Best | Avrg | Wrst | Last |
|------------------------------------------------|------|------|------|------|------|------|
|          Wireless_Broadband_Router.home -    0 |   20 |   20 |    3 |    6 |   17 |    5 |
|    L100.PHLAPA-VFTTP-81.verizon-gni.net -    0 |   20 |   20 |    8 |   24 |  180 |   13 |
|  G0-6-1-5.PHLAPA-LCR-21.verizon-gni.net -    0 |   20 |   20 |   12 |   17 |   26 |   17 |
|      ae0-0.PHIL-BB-RTR1.verizon-gni.net -    0 |   20 |   20 |   10 |   26 |   68 |   12 |
|           0.xe-6-1-1.XL3.IAD8.ALTER.NET -    0 |   20 |   20 |   17 |   24 |   52 |   19 |
|       TenGigE0-4-0-0.GW1.IAD8.ALTER.NET -    0 |   20 |   20 |   17 |   25 |   49 |   21 |
|       teliasonera-gw.customer.alter.net -    7 |   16 |   15 |   16 |   18 |   22 |   17 |
|                  ash-bb4-link.telia.net -    0 |   20 |   20 |   15 |   18 |   27 |   19 |
|                  nyk-bb2-link.telia.net -    0 |   20 |   20 |   20 |   34 |   95 |   21 |
|                   nyk-b6-link.telia.net -    0 |   20 |   20 |   20 |   25 |   41 |   22 |
|digitalocean-ic-302768-nyk-b6.c.telia.net -   0 |   20 |   20 |   16 |   21 |   32 |   21 |
|                         192.241.164.238 -    0 |   20 |   20 |   19 |   25 |   52 |   21 |
|________________________________________________|______|______|______|______|______|______|
```
   WinMTR v0.92 GPL V2 by Appnor MSP - Fully Managed Hosting & Cloud Provider

---

### Post by Doug S on 2014-04-21
Just and observation: You are using a bit of swap space, and things can really slow down when swapping is involved.

---

### Post by dave-davemackey on 2014-04-21
Thanks for the suggestions. After working with the hosting provider a bit, they determined that the virtualization host is having some hardware problems, so I'll be migrating to a new host.
Dave

---

### Post by sandyd on 2014-04-21
> **Doug S said:**
> Just and observation: You are using a bit of swap space, and things can really slow down when swapping is involved.

he still has 241300 kb free ram.

---

### Post by Doug S on 2014-04-21
> **sandyd said:**
> he still has 241300 kb free ram.yes, when the snapshot was taken. However swap was used at some point, albeit not much.

---

### Post by SeijiSensei on 2014-04-21
Linux swaps some portions of the kernel if swap is available. It's usually a small amount; on this machine with 8 GB of physical memory, I still have 20MB of swap in use.  If you run "ps aux", you'll see a bunch of processes with PIDs <  100 and an entry in square brackets.  I'm pretty sure all of these reside in swap.

---

### Post by Doug S on 2014-04-22
> **SeijiSensei said:**
> Linux swaps some portions of the kernel if swap is available. It's usually a small amount; on this machine with 8 GB of physical memory, I still have 20MB of swap in use.  If you run "ps aux", you'll see a bunch of processes with PIDs <  100 and an entry in square brackets.  I'm pretty sure all of these reside in swap.Interesting, and contrary to my experience. My servers, at least the ones that have a decent amount of memory, never seem to use any swap space at all. Of course my minimum requirements test server with only 128 megabytes of memory uses some during boot up. I even tried to increase the "swapiness" of a server to 100, and it still didn't use any swap space.```
echo "100" | sudo tee /proc/sys/vm/swappiness
```

---

