---
title: "Ubuntu Server 12.04lts unexpected reboot under Hyper-V"
date: 2015-01-13
forum: Virtualisation
---

### Post by frederic2 on 2015-01-13
Hello, 

I have an Ubuntu Server 12.04lts running in a virtual machine under Hyper-V 2012 R2. 
This server is used as LAMP platform. It works well but sometimes restarts unexpectedly. System restarts are quite random, but typically several times a week. 
There is no disc, memory or CPU usage problems. 
Software is up to date and kernel version is 3.2.0-74-generic
Virtualization host is OK, it runs 6 other virtual machines without any problem. I have another Ubuntu Server 14.04lts (doing nothing) that is up for 96 days on the same virtualization host. 
When watching boot.log, kern.log and syslog, I can only see that system has restarted without prior shutdown. 
Sometimes (rarely), virtual machine freezes when restarting, I have to power it down and up to restart. 
Do you have any idea of what is causing this, and what can I do to log system activity that causes crash. 

Thank you
Frederic

---

### Post by TheFu on 2015-01-19
So ... it has been 6 days and no attempted answers.  It is just that most of the folks here don't use Hyper-V. I've tried almost every virtualization tool out there for x86 systems, but have never, ever, even seen Hyper-V, anywhere.

I would guess that folks in these forums use:
* VirtualBox
* VMware Player/Workstation
* KVM
* Xen
* VMware ESXi
* LXC/Docker
in that order of popularity.

Sorry nobody can help here.  Rest assured that I've never seen any guest VMs crash or lock up under KVM. I have seen Ubuntu Desktop become extremely slow under VirtualBox due to Unity - but you are running server, so that isn't the cause.  

Some troubleshooting options:
You can send logs to a different host and you can boot into a liveCD, then mount the failing system to hopefully see the old logs, as the crash was happening.

Or you could switch to more popular Linux-based Virtualization. ;) Sorry - had to suggest it.

---

### Post by CharlesA on 2015-01-19
Not that it helps, but the only Linux box I've got running on HyperV is Debian Wheezy and it's running on a 2008 R2 box.

Have you tried doing a clean install of 12.04 and seeing if it exhibits the same symptoms?

My experience with KVM pretty much echos TheFu's. No issues at all.

Do you have unattended-upgrades or similar packages installed?

---

### Post by frederic2 on 2015-01-21
> **TheFu said:**
> Some troubleshooting options:
You can send logs to a different host and you can boot into a liveCD, then mount the failing system to hopefully see the old logs, as the crash was happening.
Thank you for reply. 
I have another virtual Linux server (14.04lts) that I can use for troubleshooting. Can you tell me how to send logs to this host. 

>  Or you could switch to more popular Linux-based Virtualization. ;) Sorry - had to suggest it.
Switching to another virtualization platform is not an option at the present time since I have to run several Windows VM.

---

### Post by TheFu on 2015-01-21
rsyslog is the tool for remote logging. [http://askubuntu.com/questions/186592/how-do-i-configure-rsyslog-to-send-logs-from-a-specific-program-to-a-remote-sysl](http://askubuntu.com/questions/186592/how-do-i-configure-rsyslog-to-send-logs-from-a-specific-program-to-a-remote-sysl)

kvm runs Windows inside VMs just fine, like ESXi does (actually a little better). You are not limited to whatever MSFT is selling.  But I do understand if you are mostly a MSFT shop, the desire to run their stuff.  These days, it is mostly a numbers decision, not a performance decision.  If you have 100 VMs and 51 are Windows and you have the budget, I can see staying with Windows as the hostsOS.  OTOH, if you have 51 Linux VMs, KVM or Xen is easily a great choice without having to worry about hostOS licenses. For future deployments, just something to consider.

---

### Post by frederic2 on 2015-01-21
> **CharlesA said:**
> Not that it helps, but the only Linux box I've got running on HyperV is Debian Wheezy and it's running on a 2008 R2 box.

Have you tried doing a clean install of 12.04 and seeing if it exhibits the same symptoms?

My experience with KVM pretty much echos TheFu's. No issues at all.

Do you have unattended-upgrades or similar packages installed?
There are no unattended upgrades, I run them manually. 
I can setup a clean install of 12.04, but I suspect this problem is related to the activity of server, which is a quite busy web server.

---

### Post by frederic2 on 2015-01-21
Thank you for informations about rsyslog. I shall configure it.

---

### Post by TheFu on 2015-01-21
When you say the system is freezing, do you mean the text interface cannot be typed on or have you tried to connect over ssh and that doesn't work?  I guess I'm really asking whether the network is still up and available. For desktop installs, once in a very long while, for a few people, sometimes, maybe the GUI locks up, but the underlying OS is running just fine and can be accessed through ssh to kill the X-server.

Hope that make sense.

---

### Post by CharlesA on 2015-01-21
Do you currently use a monitoring software to check the health of the machines on your network?

It's probably overkill, but setting something up like that might help you determine the cause of the lock up.

Even something as simple as a ping script to see if the host is up might help, or at least determine when the machine goes down and if it comes back up or not.

---

### Post by frederic2 on 2015-01-23
> **TheFu said:**
> When you say the system is freezing, do you mean the text interface cannot be typed on or have you tried to connect over ssh and that doesn't work?  I guess I'm really asking whether the network is still up and available. For desktop installs, once in a very long while, for a few people, sometimes, maybe the GUI locks up, but the underlying OS is running just fine and can be accessed through ssh to kill the X-server.
System freeze happens very rarely. VM has no heartbeat, VM console does not respond to keyboard in Hyper-V manager, and network is not working. This is a server, there is no GUI installed.

---

### Post by frederic2 on 2015-01-23
> **CharlesA said:**
> Do you currently use a monitoring software to check the health of the machines on your network?
Yes, server is monitored (ICMP and HTTP) every minute. 
Crash and reboot is very fast, less than 2 minutes, so downtime is not long enough to trigger an alarm.

---

### Post by TheFu on 2015-01-23
Any performance monitoring that can help?  Munin, cacti, freenms?  Something like that which captures on-machine performance data to a DB?  

I'd clone the VM at the next opportunity and start running that version to see if there's just something wrong with the specific VM storage.  If that didn't help, I'd build a new server and restore the settings, applications and data from a backup.  Ideally, these would happen on a different physical machine, but that isn't always possible.

Is there an settings file for the VM that you can post?  In libvirt, there's an XML settings file for each VM.

---

### Post by CharlesA on 2015-01-24
I would second TheFu's response of cloning the machine and seeing if the same thing happens to the clone.

If there isn't anything in the syslog to tell you why it rebooted (kernel panic?), you'll have to manually monitor it and see if there is a pattern to when it crashes.

---

### Post by frederic2 on 2015-01-24
Thank you for your suggestions. 

The VM has just crashed and I have been able to make a screen capture of console.
[ATTACH=CONFIG]259464[/ATTACH]
I am not used to decipher this, but from rapid reading, I presume that there is a kernel panic caused by Apache. 

I have also found a file named _usr_lib_apache2_mpm-prefork_apache2.0.crash in /var/crash from a previous crash. 
I am looking for information, your help is welcome.

---

### Post by TheFu on 2015-01-24
Wasn't Apache 2.0 EOL awhile ago?  I thought the normal apache on 12.04 was 2.2 and on 14.04 it is 2.4.

Perhaps a reinstall of apache is needed?  Don't know, just an idea.

Anyway ... this could be a lead when used with debug symbols and the crash dump.
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)

You can also enable system core files and debug that following a crash: [https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

---

### Post by frederic2 on 2015-01-24
Installed Apache version is 2.2.22
Thank you for the links, I shall read them.

---

### Post by CharlesA on 2015-01-24
apache2 is just the service name for both apache2.2 and 2.4.

It honestly looks like a kernel panic triggered by apache. Are there any OOM (out of memory) error? Does the syslog mention anything about OOM?

How much memory does this system have?

---

### Post by frederic2 on 2015-01-25
System have 8 GB RAM and the memory usage that I can see in htop is below 2 GB. swap is not used. 
A few months ago, I  have had OOM errors caused by badly written SQL queries in a web site,  and the consequence was that either apache2 or mysqld process was killed, but the system did  not crash. 
There is nothing about oom in syslog, I get traces of normal activity (cron, postfix) then kernel start messages.

---

### Post by sergi9 on 2015-01-25
I have the same problem, 12.04 LTS, 8GB, busy web server, rebooting every now and then.
We get the thing a bit more stable after upgrading to kernel 3.2.0-75 (I see that yours it's 3.2.0-75) but now (few minutes ago) has just rebooted after 10 days and 3 hours, so we have to look again causes and try to improve it :\

At least we aren't alone...

Cheers

Sergi

---

### Post by frederic2 on 2015-01-25
Nice to know we are not alone, too, but this does not fix the problem, that does not seem related to virtualization. 
I think I shall build another VM under 14.04lts and migrate web sites to this server.

---

### Post by sergi9 on 2015-01-25
We are pretty sure that it's something related with newer kernels and Hyper-V when we have some kind of CPU/IO/MEM/whatever pressure

Going from 3.2.0-73 to -74 improved a bit, at least reduced the frequency of panics, and from -74 to -75 we had 10 days without any panic. We have other servers like this but in other environments and didn't found any panics yet. We didn't have enough control on this server until the panics started, so we are unable to say when those panics began :(, but should be about this past November/December 

For instance we have enabled tiering and dedupe at the HyperV layer, tiering is pretty scheduled and never had any problem when tiering was running, but dedupe runs in background. We are unable to correlate anything between dedupe and panics on this server (other 12.04 are running on the same HyperV but aren't as busy as this one), but maybe there is something related. Do you have dedupe enabled on the Hyper-V?

---

### Post by frederic2 on 2015-01-26
This server is installed since november 2012 and has crashed from the beginning, but I have noticed that crash frequency depends on kernel version. However, I did not keep an history, and server activity has increased with time. 
It is an Hyper-V basic setup, no tiering and no dedupe. System and database vhd are stored on SSD, and web data files vhd are stored on hard disk.

---

### Post by CharlesA on 2015-01-26
I'm sure this doesn't help, but here's the uprecords for the wheezy box I have running off HyperV. Maybe the kernel version will tell you something?

It was originally running Squeeze, and got upgraded to Wheezy shortly after release.

```
root@Debian:~# uprecords -m 30
     #               Uptime | System                                     Boot up
----------------------------+---------------------------------------------------
     1   106 days, 09:59:23 | Linux 2.6.32-5-amd64      Wed Oct 31 00:11:15 2012
     2    78 days, 02:59:38 | Linux 3.2.0-4-amd64       Fri Nov 22 03:53:30 2013
     3    76 days, 22:26:14 | Linux 3.2.0-4-amd64       Sat Feb  8 06:45:44 2014
     4    63 days, 20:56:28 | Linux 2.6.32-5-amd64      Thu Feb 14 08:27:22 2013
     5    50 days, 00:01:19 | Linux 3.2.0-4-amd64       Tue Jul 29 06:35:31 2014
     6    47 days, 22:23:05 | Linux 2.6.32-5-amd64      Fri Aug 24 07:30:38 2012
     7    43 days, 22:47:24 | Linux 3.2.0-4-amd64       Thu Aug 29 07:01:45 2013
     8    40 days, 21:42:51 | Linux 3.2.0-4-amd64       Fri Jul 19 09:12:08 2013
     9    40 days, 08:10:30 | Linux 3.2.0-4-amd64       Sat Oct 12 09:00:46 2013
    10    38 days, 01:05:06 | Linux 3.2.0-4-amd64       Sat Nov  1 06:37:59 2014
    11    34 days, 02:36:06 | Linux 3.2.0-4-amd64       Sat Jun 15 06:33:36 2013
    12    30 days, 23:59:51 | Linux 3.2.0-4-amd64       Wed Sep 17 06:28:30 2014
    13    29 days, 00:02:04 | Linux 3.2.0-4-amd64       Wed Dec 17 06:41:51 2014
    14    28 days, 00:20:33 | Linux 3.2.0-4-amd64       Thu May 16 06:28:26 2013
    15    28 days, 00:01:38 | Linux 3.2.0-4-amd64       Thu Jun  5 06:42:15 2014
    16    22 days, 23:55:17 | Linux 3.2.0-4-amd64       Tue May 13 06:48:30 2014
    17    21 days, 23:53:51 | Linux 3.2.0-4-amd64       Mon Jul  7 06:46:48 2014
    18    18 days, 07:41:09 | Linux 2.6.32-5-amd64      Fri Apr 19 07:19:42 2013
    19    17 days, 00:07:19 | Linux 3.2.0-4-amd64       Sat Apr 26 06:41:05 2014
    20    14 days, 00:20:18 | Linux 3.2.0-4-amd64       Sat Oct 18 06:21:27 2014
    21    11 days, 11:07:44 | Linux 2.6.32-5-amd64      Fri Oct 19 13:06:56 2012
->  22    11 days, 05:23:28 | Linux 3.2.0-4-amd64       Thu Jan 15 06:33:29 2015
    23     8 days, 03:42:37 | Linux 2.6.32-5-amd64      Thu Oct 11 08:09:34 2012
    24     8 days, 00:04:05 | Linux 3.2.0-4-amd64       Tue Dec  9 06:40:25 2014
    25     7 days, 15:00:57 | Linux 3.2.0-4-amd64       Wed May  8 15:29:30 2013
    26     3 days, 23:55:16 | Linux 3.2.0-4-amd64       Thu Jul  3 06:37:20 2014
    27     1 day , 23:52:15 | Linux 3.2.0-4-amd64       Thu Jun 13 06:40:35 2013
    28     0 days, 17:30:40 | Linux 2.6.32-5-amd64      Tue May  7 21:56:36 2013
    29     0 days, 17:03:27 | Linux 2.6.32-5-amd64      Tue May  7 14:57:46 2013
    30     0 days, 01:57:12 | Linux 3.2.0-4-amd64       Thu Nov 21 16:12:17 2013
----------------------------+---------------------------------------------------
1up in     0 days, 05:44:17 | at                        Mon Jan 26 17:41:12 2015
t10 in    26 days, 19:41:39 | at                        Sun Feb 22 07:38:34 2015
no1 in    95 days, 04:35:56 | at                        Fri May  1 17:32:51 2015
    up   884 days, 23:07:45 | since                     Fri Aug 24 07:30:38 2012
  down     0 days, 06:18:34 | since                     Fri Aug 24 07:30:38 2012
   %up               99.970 | since                     Fri Aug 24 07:30:38 2012
```

---

