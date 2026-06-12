---
title: "Possible Issues ?"
date: 2014-10-21
forum: Security
---

### Post by mark-lamorey on 2014-10-21
I'm wondering if I have any issues.
First if I look at my crontab via [ crontab -l ] it is empty, but in the syslog output below I have some cron jobs trying to run.
Is there a different crontab for users and for root ?

Also I see that UFW is blocking some requests.

I know this is a bit random but, how can I investigate these a bit more to understand and understand my security more.

Below is the last few entries in my /var/log/syslog
-----------------------------------------------------------------------------------
Oct 21 16:17:01 TINY CRON[12330]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)Oct 21 16:24:30 TINY kernel: [25425.366615] [UFW BLOCK] IN=wlan0 OUT= MAC=zzz0 SRC=73.50.169.250 DST=192.168.1.14 LEN=100 TOS=0x00 PREC=0x20 TTL=54 ID=3910 PROTO=UDP SPT=46419 DPT=41078 LEN=80 
Oct 21 16:38:54 TINY kernel: [26289.055033] [UFW BLOCK] IN=wlan0 OUT= MAC=0xzzz0 SRC=192.168.1.21 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=30003 PROTO=2 
Oct 21 16:41:31 TINY kernel: [26446.028319] [UFW BLOCK] IN=wlan0 OUT= MAC=zzz0 SRC=84.248.126.80 DST=192.168.1.14 LEN=94 TOS=0x00 PREC=0x20 TTL=113 ID=22252 PROTO=UDP SPT=51858 DPT=41078 LEN=74 
Oct 21 17:00:24 TINY kernel: [27578.119805] [UFW BLOCK] IN=wlan0 OUT= MAC=zzz0 SRC=162.233.2.57 DST=192.168.1.14 LEN=100 TOS=0x00 PREC=0x20 TTL=49 ID=2485 PROTO=UDP SPT=30176 DPT=41078 LEN=80 
Oct 21 17:00:55 TINY kernel: [27609.679849] [UFW BLOCK] IN=wlan0 OUT= MAC=zzz0 SRC=162.233.2.57 DST=192.168.1.14 LEN=100 TOS=0x00 PREC=0x20 TTL=49 ID=23002 PROTO=UDP SPT=30176 DPT=41078 LEN=80 
Oct 21 17:17:01 TINY CRON[13037]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 21 18:02:14 TINY compiz: pam_ecryptfs: seteuid error
Oct 21 18:03:24 TINY kernel: [31357.104378] perf samples too long (2522 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Oct 21 18:17:01 TINY CRON[13810]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 21 19:06:05 TINY compiz: pam_ecryptfs: seteuid error
Oct 21 19:17:01 TINY CRON[14592]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 21 19:19:02 TINY compiz: pam_ecryptfs: seteuid error
Oct 21 19:27:12 TINY NetworkManager[939]: <warn> nl_recvmsgs() error: (-33) Dump inconsistency detected, interrupted

---

### Post by mark-lamorey on 2014-10-21
So, I also did a sudo crontab -l and it is similarly empty.
I searched a bit an realize that this is most likely the kernel cron engine calling the cron.hourly file where any of my cron jobs would reside.

Probably too many lines from my SYSLOG and I'll make different post to tackle each one.

---

### Post by untrustytahr on 2014-10-22
I know it can be painful to read the man page sometimes, but it does quite often answer things:
man cron-

cron  also reads /etc/crontab, which is in a slightly different format (see  crontab(5)).  In Debian, the content of /etc/crontab is predefined to  run  programs under  /etc/cron.hourly, /etc/cron.daily, /etc/cron.weekly  and /etc/cron.monthly

Also, the log file tells you exactly what program was run... cd / && run-parts --report /etc/cron.hourly

which translates to changing the working directory to root and run the run-parts utility.... Before you ask... man run-parts.

As for the firewall, the traffic is from an 'external' address to a non-routable 'internal' address, which means it went through a nat firewall.  Check the port forwarding rules & and Upnp in the router to figure out why the packets got through.

---

