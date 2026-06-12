---
title: "Ubuntu server 20.04 runnign slow"
date: 2020-10-28
forum: Server Platforms
---

### Post by patdundee on 2020-10-28
Hi Guys

I have a clean install of Ubuntu Server 20.04 LTS and it is running very slow in SSH and Webmin. There is nothing running on the server but still it runs so slow
Please see image below which shows useage and other details with nothing running on it. You will see CPU / Mem useage. 

Any ideas on why this would be extremely slow on SSH. Even accessing through SSH takes 2 or 3 minutes to log in. Update and upgrade packages from cmd line takes forever and webmin takes a long time to do anything.

Apart from Webmin the only other items installed is LAMP standard installation




Any advice would be greatly appreciated

Many thanks in advance

---

### Post by TheFu on 2020-10-28
The image doesn't help and wastes bandwidth. Please edit that post.  The **inxi -Fz** command will provide much more useful information. You'll probably need to install that package. It is in the standard repos.

Systems can be slow for hundreds of different reasons.  Check the log files.  System logs are usually in /var/log/. Look for errors and warnings. I'd use:
```
sudo egrep -i 'err|warn' /var/log/*g
```
to search quickly, but there are lots of different ways.

"Slow" is subjective.
Bad RAM or a poor connection
Bad PSU
Failing NIC. Failing network cables. Misconfigured switch, router, or failing ports.
Failing disk controller, failing SAS/SATA cables, failing disks, SSDs near EoL.
Misconfiguration, especially networking and DNS.  A slow DNS and make an entire systems be slow, but usually only for the initial connection.

So, after you figure out which subsystem is "slow", you can start to simplify and test that subsystem. Try different cables, reseat any connections, hardware, remove unused connections. For example, I have a 35-in-1 USB memory reader with 4 USB2 ports.  When that is connected to the system here, boot times skyrocket from 45 seconds to 4+ minutes.  This is because the BIOS wants to check each slot/port for a boot record.

Is anything besides ssh slow? How are local logins?  If only networking is slow, there's the subsystem to research.
**ssh -vvvv** from a client can provide help.  Are you using DNS or IP addresses?  With an IP address, a slow/misconfigured DNS won't slow things down.

---

### Post by QIII on 2020-10-28
Moved to Server Platforms.

---

### Post by ActionParsnip on 2020-10-29
What is the output of:
```

top -n 1

```
whilst the system is "slow"

---

### Post by ActionParsnip on 2020-10-29
Also please give specs for RAM and CPU and disk. Stating RAID levels and controllers where necessary

---

### Post by patdundee on 2020-10-29
Hi Action
Specs are 
32GB Ram
CPU INTEL XEON L5420 2.50GHZ 8 Cores
DISK is SSD 450GB 
NO Raid

Output is
  
    ```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
  14193 root      20   0    3976   2960   2732 S  39.1   0.0   0:00.09 sh
  14194 root      20   0    5180   1044    856 S  13.0   0.0   0:00.03 vmstat
  14192 root      20   0    8044   3924   3360 R   8.7   0.0   0:00.14 top
      1 root      20   0  169604  11660   8436 S   4.3   0.0   0:58.54 systemd
  14190 root      20   0   42516  36908   6520 S   4.3   0.1   0:00.93 /usr/share/webm
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.22 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-kblockd
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq
      9 root      20   0       0      0      0 S   0.0   0.0   0:00.74 ksoftirqd/0
     10 root      20   0       0      0      0 I   0.0   0.0   0:21.38 rcu_sched
     11 root      rt   0       0      0      0 S   0.0   0.0   0:03.97 migration/0
     12 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0
     15 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1
     16 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1
     17 root      rt   0       0      0      0 S   0.0   0.0   0:04.78 migration/1
     18 root      20   0       0      0      0 S   0.0   0.0   0:00.36 ksoftirqd/1
     20 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-kblockd
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2
     23 root      rt   0       0      0      0 S   0.0   0.0   0:04.79 migration/2
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.71 ksoftirqd/2
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-kblockd
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3
     29 root      rt   0       0      0      0 S   0.0   0.0   0:01.13 migration/3
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.46 ksoftirqd/3
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-kblockd
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/4
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/4
     35 root      rt   0       0      0      0 S   0.0   0.0   0:04.73 migration/4
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.33 ksoftirqd/4
     38 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/4:0H-kblockd
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/5
     40 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/5
     41 root      rt   0       0      0      0 S   0.0   0.0   0:04.73 migration/5
     42 root      20   0       0      0      0 S   0.0   0.0   0:00.54 ksoftirqd/5
     44 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/5:0H-kblockd
     45 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/6
```

---

