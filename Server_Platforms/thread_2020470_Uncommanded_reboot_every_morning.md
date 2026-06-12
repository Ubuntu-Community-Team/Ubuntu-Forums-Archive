---
title: "Uncommanded reboot every morning"
date: 2012-07-08
forum: Server Platforms
---

### Post by mpcookson on 2012-07-08
I've searched the forums and Google and haven't been able to find a solution other than "bad hardware?" to this issue, and I'm pretty sure this isn't a hardware issue, it's far too regular.

My 11.10 Server is rebooting every day at about 8:14am, and I've not been able to figure out why.  I've uninstalled non-critical apps and verified that the hardware is stable -- it's a clean reboot not a hard power off due to over heating or crashing.

This is a sample from last -x:

```
runlevel (to lvl 2)   3.0.0-22-server  Sun Jul  8 08:12 - 08:29  (00:16)    
reboot   system boot  3.0.0-22-server  Sun Jul  8 08:12 - 08:29  (00:16)    
runlevel (to lvl 2)   3.0.0-22-server  Sun Jul  8 04:41 - 08:12  (03:31)    
reboot   system boot  3.0.0-22-server  Sun Jul  8 04:41 - 08:29  (03:47)    
mark     pts/0        192.168.1.115    Sat Jul  7 16:44 - 16:45  (00:00)    
runlevel (to lvl 2)   3.0.0-22-server  Sat Jul  7 15:41 - 04:41  (12:59)    
reboot   system boot  3.0.0-22-server  Sat Jul  7 15:41 - 08:29  (16:47)    
runlevel (to lvl 2)   3.0.0-22-server  Sat Jul  7 11:08 - 15:41  (04:32)    
reboot   system boot  3.0.0-22-server  Sat Jul  7 11:08 - 08:29  (21:20)    
mark     pts/2        cronus.local     Fri Jul  6 08:34 - 08:36  (00:01)    
mark     pts/0        cronus.local     Fri Jul  6 08:31 - 12:51  (04:20)    
runlevel (to lvl 2)   3.0.0-22-server  Fri Jul  6 08:30 - 11:08 (1+02:38)   
reboot   system boot  3.0.0-22-server  Fri Jul  6 08:30 - 08:29 (1+23:58)   
```It's so regular that it has to be doing this on purpose, but I don't know why or what.  Looking through /var/log/syslog shows no errors, the kernel just starts logging again:

```
Jul  8 08:09:53 atlas dhcpd: DHCPACK on 192.168.1.117 to 70:56:81:d2:1a:99 (Apple-TV) via eth0
Jul  8 08:11:26 atlas snmpd[1320]: Connection from UDP: [127.0.0.1]:44560->[127.0.0.1]
Jul  8 08:12:40 atlas kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul  8 08:12:40 atlas rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="905" x-info="http://www.rsyslog.com"] start
```There's nothing interesting in /var/log/kern.log.

The only extra software I'm running is forked-daapd and mrtg.  The system has been stable for a very long time and has only recently (as in maybe a month or two ago, I haven't been tracking this closely until now) started this rebooting behavior.

All suggestions welcome!

Thank you,
Mark

---

### Post by nothingspecial on 2012-07-10
*Thread moved to **Server Platforms**.*

---

### Post by matt_symes on 2012-07-10
Hi

Have you checked cron ? (You would expect an entry in syslog but it's still worth checking)

Have you checked atd and at for jobs ?

Kind regards

---

### Post by mpcookson on 2012-07-10
> **matt_symes said:**
> 
Have you checked cron ? (You would expect an entry in syslog but it's still worth checking)

Have you checked atd and at for jobs ?

I double checked cron with "grep -R reboot /etc/cron*" and that returned nothing, as did "grep -R reboot /var/spool/cron/*"

atq returns nothing when I run it as root.

Any other log locations that I could look at?  It's starting to get very annoying and I'm remote all this week and would rather not spend my weekend wiping and reinstalling the OS.

I forgot that I was also running Crashplan, so I've disabled it too, but that's not it since the machine has rebooted since (I was thinking Java might be to blame).  It now seems to be rebooting more often too.

Since "last reboot" shows:

```
reboot   system boot  3.0.0-22-server  Tue Jul 10 04:44 - 05:46  (01:02)    
reboot   system boot  3.0.0-22-server  Tue Jul 10 03:12 - 05:46  (02:34)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 22:00 - 05:46  (07:46)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 21:55 - 05:46  (07:51)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 16:21 - 05:46  (13:24)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 15:34 - 05:46  (14:12)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 13:23 - 05:46  (16:23)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 03:52 - 05:46 (1+01:54)   
reboot   system boot  3.0.0-22-server  Sun Jul  8 14:19 - 05:46 (1+15:27)   
reboot   system boot  3.0.0-22-server  Sun Jul  8 14:14 - 05:46 (1+15:32)   
reboot   system boot  3.0.0-22-server  Sun Jul  8 11:32 - 05:46 (1+18:14)   
reboot   system boot  3.0.0-22-server  Sun Jul  8 08:12 - 05:46 (1+21:33)   
reboot   system boot  3.0.0-22-server  Sun Jul  8 04:41 - 05:46 (2+01:05)   
reboot   system boot  3.0.0-22-server  Sat Jul  7 15:41 - 05:46 (2+14:05)   
reboot   system boot  3.0.0-22-server  Sat Jul  7 11:08 - 05:46 (2+18:37)   
reboot   system boot  3.0.0-22-server  Fri Jul  6 08:30 - 05:46 (3+21:15)   
reboot   system boot  3.0.0-22-server  Fri Jul  6 08:16 - 05:46 (3+21:30)   
reboot   system boot  3.0.0-22-server  Fri Jul  6 08:07 - 05:46 (3+21:39)   
reboot   system boot  3.0.0-22-server  Fri Jul  6 04:52 - 05:46 (4+00:53)   
reboot   system boot  3.0.0-22-server  Thu Jul  5 08:42 - 05:46 (4+21:04)   
reboot   system boot  3.0.0-22-server  Thu Jul  5 05:25 - 05:46 (5+00:21)   
reboot   system boot  3.0.0-22-server  Thu Jul  5 03:55 - 05:46 (5+01:51)   
reboot   system boot  3.0.0-22-server  Wed Jul  4 11:47 - 05:46 (5+17:59)   
reboot   system boot  3.0.0-22-server  Tue Jul  3 09:06 - 05:46 (6+20:40)   
reboot   system boot  3.0.0-22-server  Tue Jul  3 07:54 - 05:46 (6+21:51)   
reboot   system boot  3.0.0-22-server  Mon Jul  2 23:32 - 05:46 (7+06:14)   
reboot   system boot  3.0.0-22-server  Mon Jul  2 07:31 - 05:46 (7+22:15)   
```

It's not a crash -- it's an orderly shutdown, right?  I'm going crazy here, how hard can it be to track down something like this?

Is there a way to determine what packages I have installed that are not from the base install?

Thanks!

---

### Post by SlugSlug on 2012-07-10
just a thought...

[https://help.ubuntu.com/community/AutomaticSecurityUpdates/](https://help.ubuntu.com/community/AutomaticSecurityUpdates/)

---

### Post by SlugSlug on 2012-07-10
also does /var/log/auth.log  not show anything?

---

### Post by mpcookson on 2012-07-10
> **SlugSlug said:**
> just a thought...

[https://help.ubuntu.com/community/AutomaticSecurityUpdates/](https://help.ubuntu.com/community/AutomaticSecurityUpdates/)

I came across that while grep'ing /etc for "reboot" and the reboot function should be turned off:

```
// Automatically reboot *WITHOUT CONFIRMATION* if a 
// the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

```

Looking at /var/log/auth.log shows:

```
Jul 10 04:35:01 atlas CRON[1749]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 04:35:01 atlas CRON[1749]: pam_unix(cron:session): session closed for user root
Jul 10 04:44:14 atlas sshd[938]: Received signal 15; terminating.
Jul 10 04:44:14 atlas sshd[1009]: Server listening on 0.0.0.0 port 22.
Jul 10 04:44:14 atlas sshd[1009]: Server listening on :: port 22.
Jul 10 04:45:02 atlas CRON[1515]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 04:45:02 atlas CRON[1515]: pam_unix(cron:session): session closed for user root

```

The cron entries look to be for mrtg which I run for general logging of system parameters (HD space, CPU temp, etc.), but the sshd signal seems suspicious, and the system rebooted right around that time this morning:

```
root@atlas:/var/log# uptime
 06:29:06 up  1:45,  1 user,  load average: 0.52, 0.50, 0.26
root@atlas:/var/log# date
Tue Jul 10 06:29:09 CDT 2012

```

So could sshd be causing the reboot?  I have openVPN installed and the only way (in theory) to log into this server is to use openVPN to connect to the machine and then you can ssh to it.  The only open port is the VPN port:

```
root@atlas:/var/log# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp dpt:openvpn 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.8.0.0/24         
ACCEPT     all  --  10.8.0.0/24          anywhere            
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

So I seriously doubt that anyone else is logging in and rebooting the machine.  Also, looking at last shows that I'm the only one logging in, and at the times I expect, so I'm confident that no one else is doing this to me.

At first I was thinking it might be sshd causing the reboot, but I'm guessing that it's just closing down in response to the reboot/shutdown -r command being given.

As a test, I've renamed /sbin/reboot to /sbin/reboot_ and the same with shutdown, so if something is executing those commands, hopefully it will fail and maybe I'll get some logging from it and be able to track it down.

Thanks!

---

### Post by SlugSlug on 2012-07-10
pretty sure that just shows ssh shutting down due to the reboot, is there anything before that in auth.log? maybe post previous 100 lines?

---

### Post by mpcookson on 2012-07-10
> **SlugSlug said:**
> pretty sure that just shows ssh shutting down due to the reboot, is there anything before that in auth.log? maybe post previous 100 lines?

The log is just full of lines like:

Jul 10 07:25:01 atlas CRON[2301]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 07:25:01 atlas CRON[2301]: pam_unix(cron:session): session closed for user root

repeated over and over every 10 minutes, nothing interesting in there (not worth posting 100 lines of that).  I've turned off mrtg as of yesterday, so I think this is from:

cron.d/sysstat:
# Activity reports every 10 minutes everyday
5-55/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1

---

### Post by Cheesemill on 2012-07-10
Does it happen at exactly the same time every day or is there any variation? Also is there any physical access to the machine?

I had a similar problem a few years ago where one of my servers would restart at about 8.30 every night. I stayed in the office late one night to see if I could get any clues and it turned out to be the cleaner unplugging the machine to plug the hoover in!

---

### Post by mpcookson on 2012-07-10
> **Cheesemill said:**
> Does it happen at exactly the same time every day or is there any variation? Also is there any physical access to the machine?

I had a similar problem a few years ago where one of my servers would restart at about 8.30 every night. I stayed in the office late one night to see if I could get any clues and it turned out to be the cleaner unplugging the machine to plug the hoover in!

It was happening very regularly, at 8:14am every morning, but it's not quite as regular yesterday and today as it was last week.

I do have physical access (when I'm home, but I'm not currently home), but it's in a basement rack in a closed utility closet, so no one would be touching it, and definitely not touching it as regularly as it has been rebooting.  It's plugged into a UPS, so power shouldn't be an issue.  There is another device plugged into that UPS that doesn't automatically reset if it loses power, and it's never shown a problem, so power out of the UPS isn't an issue.

It is quite confusing.  Thanks for your input!

---

### Post by steeldriver on 2012-07-10
> **mpcookson said:**
> I came across that while grep'ing /etc for "reboot" and the reboot function should be turned off:

```
// Automatically reboot *WITHOUT CONFIRMATION* if a 
// the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";

```

PMJI (I know nothing about automatic updates) but have you tried UNcommenting that line? the way I'm reading it Automatic-Reboot is true by default...

---

### Post by mpcookson on 2012-07-10
> **steeldriver said:**
> PMJI (I know nothing about automatic updates) but have you tried UNcommenting that line? the way I'm reading it Automatic-Reboot is true by default...

Oh, OK, I've uncommented the Automattic-reboot = false line so that it's false, but I've run apt-get update until it returns that there's nothing left to update, so it shouldn't be updating and rebooting every day.

Looking at "last reboot" as of a few minutes ago there was another reboot:

```
reboot   system boot  3.0.0-22-server  Tue Jul 10 10:09 - 10:38  (00:28)    
reboot   system boot  3.0.0-22-server  Tue Jul 10 04:44 - 10:38  (05:53)    
reboot   system boot  3.0.0-22-server  Tue Jul 10 03:12 - 10:38  (07:25)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 22:00 - 10:38  (12:37)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 21:55 - 10:38  (12:42)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 16:21 - 10:38  (18:16)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 15:34 - 10:38  (19:03)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 13:23 - 10:38  (21:14)    
reboot   system boot  3.0.0-22-server  Mon Jul  9 03:52 - 10:38 (1+06:45)   

```

/var/log/auth.log shows:

```
Jul 10 09:55:01 atlas CRON[2986]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 09:55:01 atlas CRON[2986]: pam_unix(cron:session): session closed for user root
Jul 10 10:05:01 atlas CRON[3011]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 10:05:01 atlas CRON[3011]: pam_unix(cron:session): session closed for user root
Jul 10 10:15:10 atlas CRON[1529]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 10:15:10 atlas CRON[1529]: pam_unix(cron:session): session closed for user root
Jul 10 10:17:02 atlas CRON[1532]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 10:17:02 atlas CRON[1532]: pam_unix(cron:session): session closed for user root
Jul 10 10:25:01 atlas CRON[1557]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 10:25:01 atlas CRON[1557]: pam_unix(cron:session): session closed for user root
Jul 10 10:34:45 atlas sshd[1585]: Accepted password for mark from 10.8.0.6 port 50098 ssh2
Jul 10 10:34:45 atlas sshd[1585]: pam_unix(sshd:session): session opened for user mark by (uid=0)
Jul 10 10:35:01 atlas CRON[1707]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 10 10:35:01 atlas CRON[1707]: pam_unix(cron:session): session closed for user root

```

You can see how cron is running sysstat every 10 minutes, but then at 10:17 it runs again because the system rebooted at 10:09.

From /var/log/syslog:

```
Jul 10 10:05:01 atlas CRON[3012]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Jul 10 10:07:49 atlas dhcpd: DHCPDISCOVER from 00:25:ae:7e:99:d4 Jul 10 10:09:16 atlas kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul 10 10:09:16 atlas rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1021" x-info="http://www.rsyslog.com"] start
Jul 10 10:09:16 atlas rsyslogd: rsyslogd's groupid changed to 103
Jul 10 10:09:16 atlas rsyslogd: rsyslogd's userid changed to 101
Jul 10 10:09:16 atlas rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Jul 10 10:09:16 atlas kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 10 10:09:16 atlas kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 10 10:09:16 atlas kernel: [    0.000000] Linux version 3.0.0-22-server (buildd@komainu) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #36-Ubuntu SMP Tue Jun 12 17:56:20 UTC 2012 (Ubuntu 3.0.0-22.36-server 3.0.33)
Jul 10 10:09:16 atlas kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-22-server root=/dev/mapper/atlas-root ro

```

Any other logs I should be looking at for clues?  Obviously renaming /sbin/reboot and /sbin/shutdown didn't help, so how else can a system be commanded to reboot?

Is there a way to turn off USB via ssh?  That way I could remotely "unplug" the keyboard and UPS, just in case they're causing this.

Thanks!

---

### Post by SlugSlug on 2012-07-10
anything in kern.log?

---

### Post by SlugSlug on 2012-07-10
maybe install lm-sensors just to check over heat?

Give the ram sticks a little wobble just to make sure they are ok

---

### Post by mpcookson on 2012-07-10
> **SlugSlug said:**
> maybe install lm-sensors just to check over heat?

Give the ram sticks a little wobble just to make sure they are ok

Nothing interesting in kern.log

```
Jul 10 04:44:22 atlas kernel: [   27.839864] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul 10 04:44:23 atlas kernel: [   28.288008] eth1: no IPv6 routers present
Jul 10 04:44:31 atlas kernel: [   36.012933] init: plymouth-upstart-bridge main process (955) killed by TERM signal
Jul 10 10:09:16 atlas kernel: imklog 5.8.1, log source = /proc/kmsg started.
Jul 10 10:09:16 atlas kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 10 10:09:16 atlas kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 10 10:09:16 atlas kernel: [    0.000000] Linux version 3.0.0-22-server (buildd@komainu) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #36-Ubuntu SMP Tue Jun 12 17:56:20 UTC 2012 (Ubuntu 3.0.0-22.36-server 3.0.33)
Jul 10 10:09:16 atlas kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-22-server root=/dev/mapper/atlas-root ro

```

I was using mrtg to monitor temps and my max temp (in the last 6 months) is 65C and the average temp is 25C. I've turned off mrtg as part of the troubleshooting, but these values are as of two days ago and the reboots have been going on for longer than that.

I'll check the RAM when I get home at the end of the week, but since "last" is showing what looks like clean reboots, along with sshd showing that it's shutting down, it implies that this isn't a random power cycle caused by hardware (unless the hardware is able to fake a control-alt-delete).

Thanks!

---

### Post by SlugSlug on 2012-07-10
Did you install any UPS software / agents?

---

### Post by mpcookson on 2012-07-10
I've turned off cpufreqd too, just in case.  That might have been the last thing I enabled before I started seeing these reboots.  Fingers crossed...

---

### Post by mpcookson on 2012-07-10
> **SlugSlug said:**
> Did you install any UPS software / agents?

I don't think so, but I'm wondering about that (it's been like a year since I set up this system, so my memory is hazy).  Is there a way to check installed packages?

See anything suspicious?

```
root@atlas:~# ps -ef
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 10:08 ?        00:00:00 /sbin/init
root         2     0  0 10:08 ?        00:00:00 [kthreadd]
root         3     2  0 10:08 ?        00:00:00 [ksoftirqd/0]
root         4     2  0 10:08 ?        00:00:00 [kworker/0:0]
root         5     2  0 10:08 ?        00:00:00 [kworker/u:0]
root         6     2  0 10:08 ?        00:00:00 [migration/0]
root         7     2  0 10:08 ?        00:00:00 [migration/1]
root         8     2  0 10:08 ?        00:00:00 [kworker/1:0]
root         9     2  0 10:08 ?        00:00:00 [ksoftirqd/1]
root        10     2  0 10:08 ?        00:00:00 [kworker/0:1]
root        11     2  0 10:08 ?        00:00:00 [cpuset]
root        12     2  0 10:08 ?        00:00:00 [khelper]
root        13     2  0 10:08 ?        00:00:00 [netns]
root        15     2  0 10:08 ?        00:00:00 [sync_supers]
root        16     2  0 10:08 ?        00:00:00 [bdi-default]
root        17     2  0 10:08 ?        00:00:00 [kintegrityd]
root        18     2  0 10:08 ?        00:00:00 [kblockd]
root        19     2  0 10:08 ?        00:00:00 [ata_sff]
root        20     2  0 10:08 ?        00:00:00 [khubd]
root        21     2  0 10:08 ?        00:00:00 [md]
root        22     2  0 10:08 ?        00:00:00 [kworker/1:1]
root        23     2  0 10:08 ?        00:00:00 [khungtaskd]
root        24     2  0 10:08 ?        00:00:00 [kswapd0]
root        25     2  0 10:08 ?        00:00:00 [ksmd]
root        26     2  0 10:08 ?        00:00:00 [khugepaged]
root        27     2  0 10:08 ?        00:00:00 [fsnotify_mark]
root        28     2  0 10:08 ?        00:00:00 [ecryptfs-kthrea]
root        29     2  0 10:08 ?        00:00:00 [crypto]
root        37     2  0 10:08 ?        00:00:00 [kthrotld]
root        38     2  0 10:08 ?        00:00:00 [scsi_eh_0]
root        39     2  0 10:08 ?        00:00:00 [scsi_eh_1]
root        41     2  0 10:08 ?        00:00:00 [scsi_eh_2]
root        42     2  0 10:08 ?        00:00:00 [scsi_eh_3]
root        45     2  0 10:08 ?        00:00:00 [kworker/u:5]
root       164     2  0 10:08 ?        00:00:00 [scsi_eh_4]
root       223     2  0 10:08 ?        00:00:00 [kdmflush]
root       237     2  0 10:08 ?        00:00:00 [kdmflush]
root       272     2  0 10:08 ?        00:00:00 [flush-252:0]
root       273     2  0 10:09 ?        00:00:01 [jbd2/dm-0-8]
root       274     2  0 10:09 ?        00:00:00 [ext4-dio-unwrit]
root       332     1  0 10:09 ?        00:00:00 upstart-udev-bridge --daemon
root       335     1  0 10:09 ?        00:00:00 udevd --daemon
root       414   335  0 10:09 ?        00:00:00 udevd --daemon
root       475     2  0 10:09 ?        00:00:00 [kpsmoused]
root       722     1  0 10:09 ?        00:00:00 upstart-socket-bridge --daemon
root       844     2  0 10:09 ?        00:00:00 [jbd2/sdc1-8]
root       845     2  0 10:09 ?        00:00:00 [ext4-dio-unwrit]
root       859     1  0 10:09 ?        00:00:00 dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth1.pid -lf /var/lib/dhcp3/dhclient.eth1.leases -1 e
root       885     2  0 10:09 ?        00:00:00 [jbd2/sdd1-8]
root       886     2  0 10:09 ?        00:00:00 [ext4-dio-unwrit]
root       992     1  0 10:09 ?        00:00:00 smbd -F
root      1000     1  0 10:09 ?        00:00:00 /usr/sbin/sshd -D
root      1011     1  0 10:09 ?        00:00:00 /usr/sbin/vsftpd
root      1015     1  0 10:09 ?        00:00:00 nmbd -D
102       1016     1  0 10:09 ?        00:00:00 dbus-daemon --system --fork --activation=upstart
root      1019   992  0 10:09 ?        00:00:00 smbd -F
syslog    1021     1  0 10:09 ?        00:00:00 rsyslogd -c5
avahi     1050     1  0 10:09 ?        00:00:00 avahi-daemon: running [atlas.local]
avahi     1051  1050  0 10:09 ?        00:00:00 avahi-daemon: chroot helper
root      1066     1  0 10:09 tty4     00:00:00 /sbin/getty -8 38400 tty4
root      1070     1  0 10:09 tty5     00:00:00 /sbin/getty -8 38400 tty5
root      1077     1  0 10:09 tty2     00:00:00 /sbin/getty -8 38400 tty2
root      1078     1  0 10:09 tty3     00:00:00 /sbin/getty -8 38400 tty3
root      1082     1  0 10:09 tty6     00:00:00 /sbin/getty -8 38400 tty6
root      1091     1  0 10:09 ?        00:00:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root      1095     1  0 10:09 ?        00:00:00 cron
daemon    1096     1  0 10:09 ?        00:00:00 atd
root      1098     1  0 10:09 ?        00:00:00 /usr/sbin/irqbalance
bind      1103     1  0 10:09 ?        00:00:00 /usr/sbin/named -u bind
root      1148     1  0 10:09 ?        00:00:00 /usr/sbin/openvpn --writepid /var/run/openvpn.server.pid --daemon ovpn-server --cd /etc/openvpn --conf
nobody    1157     1  0 10:09 ?        00:00:00 /usr/sbin/openvpn --writepid /var/run/openvpn.server.pid --daemon ovpn-server --cd /etc/openvpn --conf
root      1213     1  0 10:09 ?        00:00:00 ddclient - sleeping for 22751 seconds
dhcpd     1228     1  0 10:09 ?        00:00:00 /usr/sbin/dhcpd -q -pf /var/run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.conf eth0
root      1253     1  0 10:09 ?        00:00:00 /usr/bin/perl -w /usr/bin/mrtg /etc/mrtg/mrtg.cfg
ntp       1300     1  0 10:09 ?        00:00:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 111:119
root      1305   335  0 10:09 ?        00:00:00 udevd --daemon
snmp      1331     1  0 10:09 ?        00:00:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid -c /etc/snmp/snmpd.conf
root      1373     1  0 10:09 ?        00:00:00 /usr/sbin/cnid_metad -l log_note
root      1375     1  0 10:09 ?        00:00:00 /usr/sbin/afpd -U uams_dhx2.so,uams_clrtxt.so -g nobody -c 50 -n atlas
root      1417     1  0 10:09 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1420  1417  0 10:09 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1421  1417  0 10:09 ?        00:00:00 /usr/sbin/apache2 -k start
www-data  1422  1417  0 10:09 ?        00:00:00 /usr/sbin/apache2 -k start
root      1503     1  0 10:09 tty1     00:00:00 /sbin/getty -8 38400 tty1
root      2044  1000  0 11:14 ?        00:00:00 sshd: mark [priv]   
mark      2078  2044  0 11:14 ?        00:00:00 sshd: mark@pts/0    
mark      2079  2078  0 11:14 pts/0    00:00:00 -bash
root      2175  2079  0 11:14 pts/0    00:00:00 sudo su -
root      2176  2175  0 11:14 pts/0    00:00:00 su -
root      2177  2176  0 11:14 pts/0    00:00:00 -su
root      2424   992  0 11:48 ?        00:00:00 smbd -F
root      2435  2177  0 11:50 pts/0    00:00:00 ps -ef

```

---

### Post by SlugSlug on 2012-07-10
nothing stands out to me

---

### Post by mpcookson on 2012-07-10
> **SlugSlug said:**
> nothing stands out to me

OK, thanks.  Let's see if turning off cpufreqd helps...  I'll let you know tomorrow. :-)

---

### Post by mpcookson on 2012-07-10
Turning off cpufreqd didn't help, it just rebooted two minutes ago. :-(

---

### Post by SlugSlug on 2012-07-10
am hoping someone more clued up than me picks up on this post, I'd like to see how they troubleshoot it...

---

### Post by matt_symes on 2012-07-11
Hi

Reboots like this, at specific times, shout loudly of cron or at (although it may be something else).

To definitely eliminate this as a possibility, turn them off for a couple of days.

```
sudo service cron stop
``````
sudo service atd stop
```Does the PC reboot ?

You could try to disable /sbin/poweroff and /sbin/halt. 

Don't forget, you can shutdown using telinit.

Can you also post the output of

```
initctl list | sort
```EDIT: Just noticed you have snmp (simple network management protocol) running. Do you think it may be that ?

```
sudo service snmpd stop
```Kind regards

---

### Post by mpcookson on 2012-07-11
Thanks for the ideas!  I don't know about snmpd being a problem (let's hope not), but since the machine is still rebooting, I've disabled it along with cron and atd.

Here's the output you requested:

```
mark@atlas:~$ initctl list | sort
acpid start/running, process 1107
apport stop/waiting
atd stop/waiting
avahi-daemon start/running, process 1052
console-setup stop/waiting
control-alt-delete stop/waiting
cron stop/waiting
dbus start/running, process 1024
dmesg stop/waiting
failsafe stop/waiting
friendly-recovery stop/waiting
hostname stop/waiting
hwclock-save stop/waiting
hwclock stop/waiting
irqbalance start/running, process 1114
module-init-tools stop/waiting
mountall-net stop/waiting
mountall-reboot stop/waiting
mountall-shell stop/waiting
mountall stop/waiting
mounted-debugfs stop/waiting
mounted-dev stop/waiting
mounted-proc stop/waiting
mounted-run stop/waiting
mounted-tmp stop/waiting
mounted-var stop/waiting
networking stop/waiting
network-interface (eth0) start/running
network-interface (eth1) start/running
network-interface (lo) start/running
network-interface-security (networking) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/eth1) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (network-interface/tun0) start/running
network-interface (tun0) start/running
nmbd start/running, process 1026
plymouth-log stop/waiting
plymouth-splash stop/waiting
plymouth-stop stop/waiting
plymouth stop/waiting
plymouth-upstart-bridge stop/waiting
procps stop/waiting
rcS stop/waiting
rc stop/waiting
rc-sysinit stop/waiting
rsyslog start/running, process 1029
screen-cleanup stop/waiting
setvtrgb stop/waiting
smbd start/running, process 1001
ssh start/running, process 1009
tty1 start/running, process 1477
tty2 start/running, process 1091
tty3 start/running, process 1092
tty4 start/running, process 1077
tty5 start/running, process 1083
tty6 start/running, process 1096
udev-fallback-graphics stop/waiting
udev-finish stop/waiting
udevmonitor stop/waiting
udev start/running, process 350
udevtrigger stop/waiting
ufw start/running
upstart-socket-bridge start/running, process 697
upstart-udev-bridge start/running, process 347
ureadahead-other stop/waiting
ureadahead stop/waiting
vsftpd start/running, process 1013
wait-for-state stop/waiting
```

---

### Post by matt_symes on 2012-07-11
Hi

I saw you had snmp running here...

> snmp      1331     1  0 10:09 ?        00:00:00 /usr/sbin/snmpd -Lsd -Lf /dev/null -u snmp -I -smux -p /var/run/snmpd.pid -c /etc/snmp/snmpd.conf

but i could not see it listed in post #25. Did you disable it ?

Also, can you post the output of

```
cat /etc/snmp/snmpd.conf
```

I may be barking up the wrong tree here but it's worth investigation.

Kind regards

---

### Post by mpcookson on 2012-07-11
> **matt_symes said:**
> Hi

I saw you had snmp running here...

but i could not see it listed in post #25. Did you disable it ?

I probably disabled it before that was run since you asked for it to be disabled.


> Also, can you post the output of

```
cat /etc/snmp/snmpd.conf
```

I may be barking up the wrong tree here but it's worth investigation.

Kind regards

Here you go:

```
root@atlas:~# cat /etc/snmp/snmpd.conf
rocommunity  public
access MyROSystem "" any noauth exact all none none

disk /
disk /mnt/bigraid
disk /mnt/lilraid

```

The system just rebooted itself 21 minutes ago. :-(

Thanks for your help with this!

---

### Post by mpcookson on 2012-07-11
> **mpcookson said:**
> The system just rebooted itself 21 minutes ago. :-(

Looks like it just went down for the count a few minutes ago. :-(  I lost the connection a couple of minutes ago and I can't reopen a VPN connection.

I'll have to get the wife to look at the local monitor tonight if it doesn't suddenly start working (which seems unlikely at this point).

---

### Post by matt_symes on 2012-07-11
Hi

What time is it where you are now ? i.e. what time did  the server just go down ?

Kind regards

---

### Post by mpcookson on 2012-07-11
> **matt_symes said:**
> Hi

What time is it where you are now ? i.e. what time did  the server just go down ?

Kind regards

It's 16:37 at the server's location (which isn't where I am, unfortunately).  The server rebooted at 16:06 which is when I got you the above snmp.conf output and then went down for the count some time around 16:29.

---

### Post by mpcookson on 2012-07-11
> **matt_symes said:**
> Hi

What time is it where you are now ? i.e. what time did  the server just go down ?

Yay, the machine magically started working again!  This is the last -x output for everything today:

```
mark@atlas:~$ last -x
mark     pts/0        10.8.0.6         Wed Jul 11 17:24   still logged in   
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 17:08 - 17:24  (00:16)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 17:08 - 17:24  (00:16)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 16:18 - 17:08  (00:49)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 16:18 - 17:24  (01:06)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 16:15 - 16:18  (00:02)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 16:15 - 17:24  (01:08)    
mark     pts/0        10.8.0.6         Wed Jul 11 15:59 - crash  (00:16)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 15:38 - 16:15  (00:37)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 15:38 - 17:24  (01:46)    
mark     pts/0        10.8.0.6         Wed Jul 11 12:53 - 15:06  (02:13)    
mark     pts/0        10.8.0.6         Wed Jul 11 10:40 - 12:52  (02:11)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 08:47 - 15:38  (06:51)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 08:47 - 17:24  (08:37)    
mark     pts/0        10.8.0.6         Wed Jul 11 07:47 - 07:48  (00:01)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 06:47 - 08:47  (01:59)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 06:47 - 17:24  (10:37)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 06:41 - 06:47  (00:06)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 06:41 - 17:24  (10:43)    
runlevel (to lvl 2)   3.0.0-22-server  Wed Jul 11 06:37 - 06:41  (00:03)    
reboot   system boot  3.0.0-22-server  Wed Jul 11 06:37 - 17:24  (10:46)    
mark     pts/0        10.8.0.6         Wed Jul 11 05:58 - 05:59  (00:01)    

```

Any other log you would like to see?

---

### Post by matt_symes on 2012-07-11
Hi

I would look at hardware. Run a memtest on the memory and see if you can swap some out. Check the hard drive. I know you said you checked hardware, but double check.

Did you check the computers PSU voltages ?

Grep the drive for the word shutdown to see if it is in any scripts (the -r switch will reboot). 

Completely disable shutdown, poweroff, halt and reboot. Does it still reboot ?

Is it rebooting after a kernel panic as well ? It's a long shot but worth checking

Please post the output of

```
cat /proc/sys/kernel/panic*
```Can you boot into an older kernel ?

Kind regards

---

### Post by mpcookson on 2012-07-11
The output from panic*:

```
root@atlas:~# cat /proc/sys/kernel/panic*
0
0
0
0
```

I will see if I can swap out the memory, but I don't think I have any alternate sticks available.  I'll run a memtest and see what happens (though it looks like I have to have physical access to the machine to do that, so it will have to wait for the weekend).  I was going to swap out the disk this weekend if I have the time to see if that helps.

The PSU is an uber 1200W high end PS (since this is a server with 16 drives) and I'm not sure I know how to check its output, though maybe there is an snmp mib (though I have snmpd disabled now).

I've disabled /sbin/reboot,shutdown,halt,poweroff already.

I'm grep'ing the disk for shutdown now and will post back if I find a script (I've already grep'ed through /etc and didn't find anything).

Thanks!

---

### Post by matt_symes on 2012-07-11
Hi

Just be on the safe side disable /sbin/telinit as well.

...As this will also reboot the PC.

```
sudo telinit 6
```

Your kernel parameters should not cause a reboot either. That was a long shot though.

I am really beginning to suspect hardware.

EDIT: have you installed mce ? It may give information if it is a hardware error.

```
sudo apt-get install mcelog
```Kind regards

---

### Post by mpcookson on 2012-07-12
> **matt_symes said:**
> Hi

Just be on the safe side disable /sbin/telinit as well.

...As this will also reboot the PC.

```
sudo telinit 6
```

So for grins, I tested "telinit 6" and the server rebooted and has yet to come back up (which was a lot like last night).  I'm hoping that it will come back in an hour or so (like last night), but it's already been down for about an hour, so I'm starting to worry it might not come back.  It's running off of a small SSD, so I wonder if that's gone flaky for some reason.

> Your kernel parameters should not cause a reboot either. That was a long shot though.

I am really beginning to suspect hardware.

EDIT: have you installed mce ? It may give information if it is a hardware error.

```
sudo apt-get install mcelog
```Kind regards

If the machine comes back I'll install mcelog.

Thanks for your help!

---

### Post by robgr85 on 2012-07-12
I'm not sure, if it could be caused by some broken hardware (I believe that reboots would not be so regular). 

There were ideas of cron and at. Maybe You have some tasks scheduled through anacron?

---

### Post by mpcookson on 2012-07-12
> **matt_symes said:**
> Hi

Just be on the safe side disable /sbin/telinit as well.

...As this will also reboot the PC.

```
sudo telinit 6
```

Wow, took the machine forever to come back from the telinit 6 (which I did at 6:01, and it's now currently 16:36):

```
reboot   system boot  3.0.0-22-server  Thu Jul 12 15:40 - 16:31  (00:50)    
reboot   system boot  3.0.0-22-server  Thu Jul 12 15:18 - 16:31  (01:12)    
reboot   system boot  3.0.0-22-server  Thu Jul 12 14:54 - 16:31  (01:36)    
reboot   system boot  3.0.0-22-server  Thu Jul 12 03:58 - 06:01  (02:02)    

```

Doesn't seem like that's what happening since normally the machine reboots and is back operating in just a couple of minutes.  I which I new what took it until 14:54 to come back up (and then why it rebooted at 16:31)

> EDIT: have you installed mce ? It may give information if it is a hardware error.

```
sudo apt-get install mcelog
```Kind regards

I've now installed mcelog, what should I be looking for?  Do we need to wait for another uncommanded reboot?

Thanks!

---

### Post by matt_symes on 2012-07-12
Hi

There should be a log file generated at 

```
/var/log/mcelog
```

Check for this after a reboot to see if it has been generated.

Kind regards

---

### Post by mpcookson on 2012-07-13
> **matt_symes said:**
> Hi

There should be a log file generated at 

```
/var/log/mcelog
```

Check for this after a reboot to see if it has been generated.

Kind regards

So after disabling /sbin/telinit by renaming it to /sbin/telinit_, the system randomly rebooted and appears to no long be able to fully boot (I can't connect to it and the wife's report of the last line on the screen seems to google out as a corrupt install).

Any idea of how to extricate myself from this situation (once I get home tonight)?

Thanks!

---

### Post by matt_symes on 2012-07-13
Hi

Boot into a LiveCD/USB and enable telinit  and the others after mounting the partition, as that's really the only thing we have changed (apart from installing mce). How did you disable them BTW ? chmod ?

Post back the error message you are seeing.

This is a really odd one as it seems we have looked at all the basic possibilities. I'll have a  think.....

Unplug the PC from the network. Leave it until after it normally reboots. Does it reboot ?

Kind regards

---

### Post by Cheesemill on 2012-07-13
> **matt_symes said:**
> This is a really odd one as it seems we have looked at all the basic possibilities. I'll have a  think.....

I don't have any more suggestions but I'm intrigued as well, I've subscribed to this thread because I really want to know what's going on (from a curious sysadmins point of view).

I'm presuming you've tried memtest and let it run for several passes......

---

### Post by matt_symes on 2012-07-13
Hi

> **Cheesemill said:**
> I don't have any more suggestions but I'm intrigued as well, I've subscribed to this thread because I really want to know what's going on (from a curious sysadmins point of view).

I'm presuming you've tried memtest and let it run for several passes......

I'm glad you're looking at this as well cheesemill. I'm scratching my head.

@OP. 

Can we approach this a different way ? Is there *anything* running at the time it reboots that may cause a CPU triple fault ? Is there *anything* scheduled to run at the time it reboots ?

What hardware test have you run ?

Post back *full* logs before it rebooted (dmesg, syslog).

What hardware do you have ?

```
sudo lshw
```Post this back.

Disable all services (sudo service stop) and remove (sudo modprobe -r) all non essential drivers for testing purposes.

PC's don't reboot for no reason :confused:

Kind regards

---

### Post by Cheesemill on 2012-07-13
I know you're not on-site with this machine so this will be a royal PITA but it might be worth running the machine off network for a while and seeing if the reboot still occurs.

I'm not sure exactly what this will prove but it has to narrow it down somehow :-?.

---

### Post by mpcookson on 2012-07-15
Hi All,

Thanks for all your help with this one.  Unfortunately due to travel delays I couldn't get to the machine on Friday and Saturday was a funeral so I didn't get to the machine until about 8pm Saturday night.  I ran memtest all night (it said wall clock of nearly 10 hours) and it passed and the machine was still on this morning.

I still have the rogue process theory, but I'm worried about the PATA->CF (or the CF cards) adapter so I would like to also explore copying everything to a real hard disk.  I have the copy made, but I need to fix grub so that it boots, but I don't think I'll get a chance to do that before I have to fly out at 15:00.  I'll be back on Thursday though.

I'll reply back to the other questions next, just wanted to let you all know that the memtest passed and the machine appears reasonably stable in the memtest.

Unfortunately, this machine is my file server, dhcp server, and router so turning it off or killing all of the services isn't an option.

---

### Post by mpcookson on 2012-07-15
> **matt_symes said:**
> Hi

Boot into a LiveCD/USB and enable telinit  and the others after mounting the partition, as that's really the only thing we have changed (apart from installing mce). How did you disable them BTW ? chmod ?

Post back the error message you are seeing.

This is a really odd one as it seems we have looked at all the basic possibilities. I'll have a  think.....

Unplug the PC from the network. Leave it until after it normally reboots. Does it reboot ?

Kind regards

I got the system booting again using the LiveCD (and googling how to mount a lvm) and I was able to rename telinit (I had renamed it to telinit_ along with halt, reboot, poweroff, etc.) back and the system rebooted and is back up (which is why I'm able to get to the web again).

There is no output in /var/log/mcelog (it's still 0 bytes), so I guess we can assume that it didn't reboot because of a hardware fault.

---

### Post by mpcookson on 2012-07-15
> **matt_symes said:**
> @OP. 

Can we approach this a different way ? Is there *anything* running at the time it reboots that may cause a CPU triple fault ? Is there *anything* scheduled to run at the time it reboots ?

What hardware test have you run ?

I ran memtest last night.  It reported no errors and the machine was on for almost 10 hours before I rebooted it to Ubuntu (it's my dhcp server and router, so I need it).

There is nothing, that I am aware of, scheduled to run (beyond the default).  I've emptied all of the cron jobs that I installed (which was only mrtg which had been running for months before there was a problem).  I'm left with just the system defaults (11.10 server).

I only run openVPN, dhcp3, ssh-server, mrtg (now in daemon mode rather than cron mode, but when it was turned off altogether things were still rebooting so it's back on again), samba, netatalk, forked-daapd (iTunes share, now turned off), and CrashPlan (now off, along with java).  I'm running 11.10 server in CLI-only mode.  It's running from a PATA<->CF adapter on two 8GB CF cards that are LVM'ed together to be one volume.  It's been this way since early January and hasn't been a problem until recently.  I have a small HD that I want to copy it over to, but I don't have the time to do that this week (since LVM makes the copy so much more complicated).  I've made a full cp -r of the CF drive, but grub on the HD is unhappy, so I need to fix that up, which I'm guessing is next weekend's job.

> Post back *full* logs before it rebooted (dmesg, syslog).

What hardware do you have ?

```
sudo lshw
```Post this back.

Disable all services (sudo service stop) and remove (sudo modprobe -r) all non essential drivers for testing purposes.

PC's don't reboot for no reason :confused:

Kind regards

I've attached kern.log and dmesg in logs.zip and syslog had to be uploaded by itself because it's large.  The mcelog is empty so it's not attached.  I renamed them to have .txt for the purposes of the upload. Let me know if there is another log you would like to see.

Thanks again for all your help with this!

---

### Post by mpcookson on 2012-07-15
> **matt_symes said:**
> Disable all services (sudo service stop) and remove (sudo modprobe -r) all non essential drivers for testing purposes.

PC's don't reboot for no reason :confused:

Kind regards

These are the modules that are running:

```
mark@atlas:/var/log$ lsmod
Module                  Size  Used by
xt_tcpudp              12603  1 
xt_state               12578  1 
xt_conntrack           12760  1 
iptable_filter         12810  1 
ipt_MASQUERADE         12759  2 
nf_nat_ftp             12704  0 
iptable_nat            13229  1 
nf_nat                 25890  3 ipt_MASQUERADE,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      19716  5 iptable_nat,nf_nat
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_irc       13383  0 
nf_conntrack_ftp       13452  1 nf_nat_ftp
nf_conntrack           82342  9 xt_state,xt_conntrack,ipt_MASQUERADE,nf_nat_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4,nf_conntrack_irc,nf_conntrack_ftp
ip_tables              27473  2 iptable_filter,iptable_nat
x_tables               29846  7 xt_tcpudp,xt_state,xt_conntrack,iptable_filter,ipt_MASQUERADE,iptable_nat,ip_tables
hid_apple              13375  0 
psmouse                73882  0 
asus_atk0110           18078  0 
serio_raw              13166  0 
i915                  575489  1 
drm_kms_helper         42558  1 i915
drm                   236290  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19597  1 i915
lp                     17799  0 
parport                46562  1 lp
usbhid                 47198  0 
hid                    95463  2 hid_apple,usbhid
atl1c                  41681  0 
r8169                  52788  0 
hptiop                 19162  2 

```

See any that are candidates for turning off?

I'm wary of turning off all services because I need several of them, dhcp, ssh, and iptables at the very least.  Is there any way to be more selective about what's turned off?

This is all that I have in /etc/rc2.d:
```
K20cpufreqd      K99crashplan  S15bind9    S20ddclient         S20mcelog  S20router  S20sysstat              S23ntp       S50rsync      S70pppd-dns  S91apache2      S99ondemand
K25forked-daapd  README        S16openvpn  S20isc-dhcp-server  S20mrtg    S20snmpd   S20unattended-upgrades  S50netatalk  S70dns-clean  S75sudo      S99grub-common  S99rc.local

```

About the only thing that I know of that I could turn off is snmpd and mrtg, but do we really suspect that they might be the problem?  They've been on for 6 months and this is a reasonably new problem.

Thanks!

---

### Post by mpcookson on 2012-07-16
> **mpcookson said:**
> About the only thing that I know of that I could turn off is snmpd and mrtg, but do we really suspect that they might be the problem?  They've been on for 6 months and this is a reasonably new problem.

One of the things I was worried about early in this process was the UPS since it has a USB connection to the server.  I was looking for a way to remotely shut it down, but when I was home over the weekend I unplugged it.  The server has now been up for over 20 hours.  I don't want to jinx it, but maybe that's the issue?  Time will tell...

Thanks everyone!

---

### Post by matt_symes on 2012-07-16
Hi

Sorry for the delay in posting. Let's hope it's the UPS that has been causing the issue :)

EDIT. Nothing in the logs :( It does look like an external event so the UPS is the prime candidate i think.

Kind regards

---

### Post by mpcookson on 2012-07-16
> **matt_symes said:**
> Hi

Sorry for the delay in posting. Let's hope it's the UPS that has been causing the issue :)

EDIT. Nothing in the logs :( It does look like an external event so the UPS is the prime candidate i think.

Kind regards

The system has been up for over a day, which I think is longer than it has been for at least the last two months.  If it's still up this time tomorrow, I'm going to blame the UPS and start turning services on one by one.

I wonder how I can trouble shoot the UPS...  But that's a question for a different forum.

Thanks for all your time and effort on this (weird) one!

Regards,
Mark

---

### Post by mpcookson on 2012-07-17
> **mpcookson said:**
> The system has been up for over a day, which I think is longer than it has been for at least the last two months.  If it's still up this time tomorrow, I'm going to blame the UPS and start turning services on one by one.

I wonder how I can trouble shoot the UPS...  But that's a question for a different forum.

Thanks for all your time and effort on this (weird) one!

Regards,
Mark

After two days of being up will all the extra services reenabled, I'm ready to call this as an issue with the UPS.  It's either that UPS is at fault for signaling a low battery or the apc driver incorrectly understanding the state of battery.  Why, however, would a low battery cause a reboot and not a complete power off, I don't understand, but that's probably a question for a different group.

I guess we can move this into the [SOLVED] category.  Thanks for everyone's help on this one!

---

### Post by kgatan on 2012-07-18
I have a similar problem at home but not as frequent reboots. 
My ups is also to blame but it does however report both by sound and through apcupsd that the batteries need replacement. 

Depending on the brand of the ups you can use apcupsd to do some diagnostics on the ups.

---

