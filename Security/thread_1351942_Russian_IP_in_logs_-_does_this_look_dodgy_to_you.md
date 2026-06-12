---
title: "Russian IP in logs - does this look dodgy to you?"
date: 2009-12-11
forum: Security
---

### Post by cornburn on 2009-12-11
Hi everyone
 
I'm brand new, Ubuntu's been on the server for 3 or 4 days now and have been happy with many of the features. I've been having some random crashes I haven't managed to work out yet (flashing keyboard lights, kernel panic, probably hardware) Anyway, I was going through the logs looking for some clues and found the following which looked bery odd. I'm hoping someone can clear up what it is. You can see the system seemed to stop responding on the night of the 8th, until I did a hard reset on the 10th. In between the only 2 events on the 9th are something to do with an external IP (85.30.229.13). A whois shows this belongs to an ISP in Russia (and I'm in the UK). Is this something innocent or is there someone scanning for freshly installed (and possibly insecure) Ubuntu installations?
 
ME ACCESSING REMOTELY
 
Dec 8 22:22:37 motherhen kernel: [ 72.428489] sky2 eth0: enabling interface
Dec 8 22:22:37 motherhen kernel: [ 72.428625] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 8 22:22:38 motherhen kernel: [ 74.112590] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
Dec 8 22:22:38 motherhen kernel: [ 74.182101] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 8 22:22:39 motherhen kernel: [ 74.443911] [drm] DAC-6: set mode 1024x768 12
Dec 8 22:44:40 motherhen kernel: [ 1396.623483] [drm] DAC-6: set mode 1280x1024 10
Dec 8 22:44:40 motherhen kernel: [ 1397.162382] [drm] DAC-6: set mode 1024x768 13
Dec 8 22:52:46 motherhen pulseaudio[2111]: pid.c: Stale PID file, overwriting.
 
DODGYNESS???
 
Dec 9 22:05:05 motherhen kernel: [85421.542691] ICMP: 85.30.229.13: Source Route Failed.
Dec 9 22:05:08 motherhen kernel: [85424.526312] ICMP: 85.30.229.13: Source Route Failed.
 
MACHINE HARD RESET AFTER CRASH
 
Dec 10 12:17:02 motherhen kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 10 12:17:02 motherhen rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="884" x-info="[http://www.rsyslog.com](http://www.rsyslog.com)"] (re)start
Dec 10 12:17:03 motherhen rsyslogd: rsyslogd's groupid changed to 102
Dec 10 12:17:03 motherhen rsyslogd: rsyslogd's userid changed to 101
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Initializing cgroup subsys cpuset
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Initializing cgroup subsys cpu
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
Dec 10 12:17:03 motherhen kernel: [ 0.000000] KERNEL supported cpus:
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Intel GenuineIntel
Dec 10 12:17:03 motherhen kernel: [ 0.000000] AMD AuthenticAMD
Dec 10 12:17:03 motherhen kernel: [ 0.000000] NSC Geode by NSC
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Cyrix CyrixInstead
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Centaur CentaurHauls
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Transmeta GenuineTMx86
Dec 10 12:17:03 motherhen kernel: [ 0.000000] Transmeta TransmetaCPU
Dec 10 12:17:03 motherhen kernel: [ 0.000000] UMC UMC UMC UMC

---

### Post by bodhi.zazen on 2009-12-11
Nothing like reading the logs to instill paranoia.

All I see are a few ping attempts ("ICMP: 85.30.229.13: Source Route Failed")

what is it that concerns you ?

---

### Post by cascade9 on 2009-12-11
> **cornburn said:**
>  Is this something innocent or is there someone scanning for freshly installed (and possibly insecure) Ubuntu installations?

IMO, scanning. Not for ubuntu in particular, more for anything. 

If you think thats bad you should see some of the logs I used to have, being hammered from Chinese IPs.

---

### Post by Jive Turkey on 2009-12-11
try this command:```
cat /var/log/auth.log | grep 85.30.229.13
```

This will show any attempts to open an ssh session if any.

---

### Post by loxety on 2009-12-11
Looks like a false positive to me.

---

### Post by teward on 2009-12-11
I agree that it's a false positive.  I get about 100 different IPs from US, Mexico, Canada, Germany, etc. every day, and they're just normal internet randomness traffic.  Use a firewall, and if your ports are configured to **not respond to requests** you'll be fine.

---

### Post by koenn on 2009-12-12
> **bodhi.zazen said:**
> Nothing like reading the logs to instill paranoia.

All I see are a few ping attempts ("ICMP: 85.30.229.13: Source Route Failed")

what is it that concerns you ?
It's not ping attempts.
"source route failed" is the ICMP msg a host sends back when it was asked to deliver/forward a source-routed packet, but failed to do so.

---

### Post by bodhi.zazen on 2009-12-12
Thank you ;)

---

### Post by cornburn on 2009-12-14
Cool, thanks for putting my mind at rest. The machine went through a kernel panic shortly afterwards so I was worried it might be related and my brand new install might be sending out a beacon to the Russian mafia after my credit card details ;)
 
It's all behind a firewall router set up to drop any pings so I'll stop worrying and get on with the 50 other things that need fixing.
 
Thanks again :)

---

