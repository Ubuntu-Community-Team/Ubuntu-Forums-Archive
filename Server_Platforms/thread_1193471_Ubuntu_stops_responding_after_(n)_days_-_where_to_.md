---
title: "Ubuntu stops responding after (n) days - where to start?"
date: 2009-06-21
forum: Server Platforms
---

### Post by gmerideth on 2009-06-21
About a year ago I replaced a number of Fedora Core machines with Ubuntu 8.10 (Linux ubuntu 2.6.27-7-server #1 SMP Tue Nov 4 20:18:35 UTC 2008 i686 GNU/Linux) and overall have been very pleased with the change.

We run 4 Ubuntu installs under ESXi that occasionally, and this is the frustrating part, just seem to stop responding to requests.  We can ping the machines but not create an SSH connection (just get rejections).  Attempting to log into the machine at the ESXi console hangs.  The run times range from 50 days to 200+

The four Ubuntu machines runs on a dual quad-core ESXi box with 2 processors virtually assigned to each install along with 1GB of memory.  ESXi shows no errors (we had timing issues with Fedora).

Where can I start digging to find out, in an event log, terminal window or anything, what could be going on here? :confused:

---

### Post by Kareeser on 2009-06-21
Hm. That's quite an odd happenning. Is the server actively rejecting NEW SSH connections? Or do existing connections continue to work even after the server becomes "unresponsive"?

To that end, I'd run "tail -F syslog" on the server through an SSH tunnel from a monitor system, and see what happens when the server suddenly goes quiet.

---

### Post by gmerideth on 2009-06-21
I started a syslog monitor on my workstation to all 4 machines and now I'll play the waiting game.  I have a report back now that an ssh connection from home to the mysql machine failed (stopped responding) when in the middle of a du command.  There appears to be no 'set' thing that Ubuntu's doing that causes this.

I'll see if the monitoring ssh sessions show anything useful when we get another freeze.

We also checked ESXi during the lockup and found that while CPU resources had dropped to <0.05% (background static) we had blips (upwards of 150k/sec) drive activity.

Some part of linux must have been operational, maybe networking froze. :confused:

---

### Post by mevans336 on 2009-07-15
I wonder if my problem is related, but I am having networking issues with Ubuntu Server, both 8.04 and 9.04, inside of ESXi. I am able to ping things on the LAN by IP as well as my gateway, but I am unable to ping past the gateway, either by name (I get a failure to resolve) or by IP address. 

I thought this was a networking issue outside of Ubuntu, but I have 30+ machines (CentOS 5.2) on the same network, some inside of the same ESXi server, that are able to communicate just fine. Installing the ESXi vmxnet driver doesn't help at all.

I'm still experimenting to try and nail down a cause, but so far it seems like the only thing that triggers it effectively is idle time.

---

### Post by rputnins on 2009-12-09
Hi!

I found this topic while searching the Internet. I have the same problem on Siemens Primergy C150 server with clean install of Ubuntu 9.10 x86 + ISPConfig3 admin panel. I have software RAID 5 with 3 scsi disks. The server stops responding when some loud is produced. Today it stopped when I tried to un-tar 300Mb archive. I was connectet to server via ssh, the ssh session froze and I am unable to open new sesion, the server actively refuses connection. I can still ping the server. The apache is also frozen, I cant access it.

I thought it was connected to server hardware or memory so I run memtest for 24 hours, no errors reported. I am suspecting the software raid or memory. I will try to install Ubuntu 8.04 LTS and I will check if I get the same problem. I have tested the server memory, cpu, motherboard with PC Check, no errors found.

I hope this is bug in Ubuntu otherwise I will need new server ](*,)

---

