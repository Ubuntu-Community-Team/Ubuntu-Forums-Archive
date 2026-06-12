---
title: "Strange gap in syslog"
date: 2010-08-07
forum: Security
---

### Post by JKyleOKC on 2010-08-07
After having been invaded two weeks ago, I took the advice offered in [http://ubuntuforums.org/showthread.php?t=1542332](http://ubuntuforums.org/showthread.php?t=1542332) post #2 and rebuilt my systems from bare metal using Xubuntu 10.04.1 Desktop. I was careful to deny all access, via ufw, while downloading the 170-plus updates required for each of the two boxes I currently have up, then restored my network configuration and iptables setup from backups.

All seems to be going well, with no suspicious activity appearing in auth-log (which I've been monitoring round the clock). However for the past two days I've been seeing a gap between syslog and syslog.1, each morning. Anacron runs cron.daily at about 7:35 a.m., which of course runs logrotate to rotate syslog. This data appears as the final entries of syslog.1 when I check it later in the morning.

However, syslog itself starts with a 7:46 a.m. entry that rsyslogd has been HUPped, followed by an entry that cron.daily has completed. Here's this morning's data:
```
Aug  7 07:46:30 mehitabel rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="814" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug  7 07:46:30 mehitabel anacron[7979]: Job `cron.daily' terminated
Aug  7 07:46:30 mehitabel anacron[7979]: Normal exit (1 job run)

```

Syslog1 shows this as its final five entries:
```
Aug  7 07:30:01 mehitabel anacron[7979]: Anacron 2.3 started on 2010-08-07
Aug  7 07:30:01 mehitabel anacron[7979]: Will run job `cron.daily' in 5 min.
Aug  7 07:30:01 mehitabel anacron[7979]: Jobs will be executed sequentially
Aug  7 07:35:01 mehitabel anacron[7979]: Job `cron.daily' started
Aug  7 07:35:01 mehitabel anacron[7988]: Updated timestamp for job `cron.daily' to 2010-08-07

```

That 11-minute gap concerns me greatly. I've not found any suspicious activity in any other log, but it's not at all usual for any of my systems to go that long without a syslog entry. I suspect that the action at 7:46:30 wiped out the log entries for that 11 minutes, and I wonder why it happened.

I've been through the /etc/cron.daily directory looking for any possible cause but have not found anything yet. I do see this same gap on both systems; one is connected to both the Internet and my LAN, to serve as the router and gateway for the LAN, while the other is only on the LAN.

I don't find any reference to rsyslogd in any of the files I've examined so far, nor does the rsyslogd man page shed any light on the "type 'lightweight'" meaning...

My question is simple: is this normal action for Lucid Lynx, or should I still be suspicious of something wrong with my systems?

---

### Post by clrg on 2010-08-08
Do you expose any services to the internet?

---

### Post by JKyleOKC on 2010-08-08
Just one: an FTP server using proftpd, which is locked down tightly. The only login permitted to it is "anonymous/ftp" and that one is chrooted, with only the "public" subdirectory being navigable. Proftpd doesn't implement the EXEC command. This server is under attack daily, but has been in use for nearly a decade.

Going back through the retained syslogs I've determined that all was working normally the morning of August 4, but the gap appears on the morning of August 5. The only unusual events shown for August 4 trace a download via Synaptic, of the grdesktop package. I was trying it out as a way to monitor my email program that runs in a VM on another box; I quickly decided that it was not what I needed, and purged it. All of this happened between 9 and 10 a.m. on August 4. I also verified from that log that the cron.daily run normally takes about 11 minutes, so the question now boils down to this:

What is sending the HUP signal to rsyslogd, and why?

---

### Post by clrg on 2010-08-08
Maybe rsyslogd was shut down for the logrotation? So that it wouldn't try to write to files being moved. Other than this, I have no idea. Sorry for not helping you further :)

---

### Post by JKyleOKC on 2010-08-08
That sounds reasonable!

This morning the gap was longer, and the new syslog showed not one but two HUP events. Since cron.weekly ran this morning, via anacron, it looks as if it's anacron itself that's doing this -- but the question still remains as to why things changed sometime on August 4...

---

