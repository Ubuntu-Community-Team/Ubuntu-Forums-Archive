---
title: "CUPS starting slow with 4000 queues"
date: 2013-09-20
forum: Server Platforms
---

### Post by tobo777 on 2013-09-20
Hi everyone,

I'm running a cups printserver with about 4000 queues on cups (Ubuntu 12.04, 64 bit, last patched yesterday). Ubuntu runs on a virtualized environment (ESX) VM with 2 cores, 1 GB RAM. 

The starting of cups takes about 20 minutes. After having done a reconfiguration 20 minutes are passing, too.

Since I had errors 

```

"org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus securi ty policy blocked the reply, the reply timeout expired, or the network connection was broken." 
```

I already added  

```
<limit name="max_connections_per_user">512</limit>

```


to ```
 /etc/dbus-1/system.conf 
```.

looking on htop-output, I see that ony 1 core is used.

Is there an option to speed up the start? 

Yours tobo

---

### Post by tgalati4 on 2013-09-20
Things to test:

Add more RAM to the VM.  Try 2GB and see if performance improves.
Try a different hypervisor.  Perhaps Xen will provide better performance for this use case.
The errors are not obvious, since they are not specific, but if all of the queues come up after 20 minutes, then it must be a timing issue.  Are most of these virtual print queues with only a few real, physical printers?  Or do you reallly have 4,000 printers hung on this network?  If the power-savings is agressive on these printers, then they will go to sleep and may be slow to wake to respond to the CUPS online queries.  If this is the case, then you could run a wake-up script to all printers, before a CUPS reboot.  That might speed things up.

For single core vs dual core, I would suspect the hypervisor settings, but it's possible that CUPS is only compiled for single core.  That will require some digging.

---

### Post by tobo777 on 2013-09-23
Hi,

thanks for your reply. 

I tried 2 GB RAM. No change at all. 19 minutes.

Here's the top output:

```
Tasks:  72 total,   2 running,  70 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.0%us,  0.2%sy,  0.0%ni, 49.7%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2051524k total,   567020k used,  1484504k free,    29616k buffers
Swap:  1048572k total,        0k used,  1048572k free,   109592k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
  555 root      20   0  433m 336m 2652 R  100 16.8  15:40.78 cupsd
 1398 root      20   0  163m 4608 3680 S    0  0.2   0:01.93 vmtoolsd
 1570 cups      20   0 84020 1684  844 S    0  0.1   0:00.06 sshd

```


Using another hypervisor is not possible, since ESX is the standard in our company. I see both cores eg in htop. 

I contact 20 printservers worldwide via LPR-Protocol. No single printer, so I can rule the power-saving theme out.

---

### Post by tobo777 on 2013-09-23
To additionally mention: In /var/log/cups/error_log I get 

W [23/Sep/2013:15:21:45 +0200] Avahi client failed: -26
W [23/Sep/2013:15:21:55 +0200] Avahi client failed: -26
W [23/Sep/2013:15:22:05 +0200] Avahi client failed: -26

each 10 seconds.

---

### Post by tgalati4 on 2013-09-23
Avahi daemon is a Bonjour-like printer annunciator--"Hey, look at me, I'm a printer on your network."  You either don't have avahi daemon installed, or it is not running.  You probably don't need it, since avahi is used for plug-and-play, changing, dynamic networks--like a bunch of macbooks in a hotel room.  

tgalati4@Mint14-Extensa ~ $ apt-cache policy avahi-daemon
avahi-daemon:
  Installed: 0.6.31-1ubuntu2
  Candidate: 0.6.31-1ubuntu2
  Version table:
 *** 0.6.31-1ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

I'm guessing that you are getting a timeout for each printer instance when avahi fails to respond.  That would take 20 minutes.

You will have to do some research on how to disable the avahi check in CUPS.  I believe it was turned on by default in 12.04 CUPS.  It's helpful for individual users and small groups, but it may interfere (as in this case) in an enterprise environment.

Some reading on [Upstart]("http://upstart.ubuntu.com/cookbook/#id315").  CUPS and avahi-daemon are controlled by upstart.

You can comment out the check for avahi-daemon in this thread:  [http://ubuntuforums.org/showthread.php?t=2176138](http://ubuntuforums.org/showthread.php?t=2176138)

---

