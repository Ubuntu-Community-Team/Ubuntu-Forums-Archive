---
title: "System76 running 10.10 randomly reboots/crashes"
date: 2011-02-08
forum: System76 Support
---

### Post by TMRadMan on 2011-02-08
Hi,
Twice now I have come back to my desk on Tuesday morning with my system restarted.  I look in /var/log/messages and /var/log/syslog and there is nothing interesting other than the kernel boot message:

Feb  8 05:17:01 TMR-76-LT CRON[6621]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 05:35:22 TMR-76-LT kernel: imklog 4.2.0, log source = /proc/kmsg started.
Feb  8 05:35:22 TMR-76-LT rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1079" x-info="http://www.rsyslog.com"] (re)start
Feb  8 05:35:22 TMR-76-LT rsyslogd: rsyslogd's groupid changed to 103
Feb  8 05:35:23 TMR-76-LT rsyslogd: rsyslogd's userid changed to 101
Feb  8 05:35:22 TMR-76-LT rsyslogd-2039: Could no open output file '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Feb  8 05:35:23 TMR-76-LT kernel: [    0.000000] Initializing cgroup subsys cpuset
Feb  8 05:35:23 TMR-76-LT kernel: [    0.000000] Initializing cgroup subsys cpu
Feb  8 05:35:23 TMR-76-LT kernel: [    0.000000] Linux version 2.6.35-22-generic (buildd@yellow) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 (U\
buntu 2.6.35-22.35-generic 2.6.35.4)
Feb  8 05:35:23 TMR-76-LT kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=552496e2-92cc-4e0f-87c0-322edc0cb632 ro quiet splash

This reminds me of why I got away from Windows.
My system is a System76 Pangolin Performance with
[I]Memory : 8 GB - DDR3 1333 MHz - 2 DIMMs and
[/I]*Processor : Core i7-740QM Processor ( 45nm, 6MB L3 Cache, 1.73GHz)*

I love my system, but this is a bit frustrating.  
Any thoughts on how I can track this down?
Cheers,
Tom

---

### Post by isantop on 2011-02-08
Hi Tom.

I'd like to move this into support email. In order to find out why the system rebooted, I'll need to see the rest of the log, which is cumbersome to post here. Please send us an email at support...at...system76...dot...com.

---

### Post by TMRadMan on 2011-02-08
Thanks isantop.  I will send it momentarily.

---

