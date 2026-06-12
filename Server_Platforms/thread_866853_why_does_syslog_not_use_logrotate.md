---
title: "why does syslog not use logrotate"
date: 2008-07-22
forum: Server Platforms
---

### Post by ssam on 2008-07-22
most log files in /var/log seem to be rotated by logrotate and can be configured either in /etc/logrotate.conf or /etc/logrotate.d

how ever syslog seems to have its own method, using /etc/cron.daily/sysklogd which uses the 'savelog' command.

is there a good reason for syslog not to use logrotate? it seems odd to have two systems to do the same jobs, and two very different methods to configure the a similar task.

---

### Post by MJN on 2008-07-22
The 'reason' is largely historical, specifically that Syslog is old - very old - and has been around for a lot longer than Logrotate. Hence, in order to keep on top of the management of log files Syslog has always been able to rotate/archives its own data....
 
Along came Logrotate designed solely to manage the logs of those apps that didn't use Syslog. Most modern systems, by virtue of them running more and more processes/daemons log a great deal more than those of yesteryear and hence there is a requirement for both Syslog and Logrotate log management.
 
To merge the functionality of two disparate packages would be difficult given the packages are designed for different things - it's just the log management function that is common to both.
 
I agree though; it can make life more difficult than it could otherwise be.
 
Mathew

---

### Post by hans.voss on 2008-10-24
This is most unfortunate for Ubuntu on laptops as the sysklod way of managing its log files creates a new file for me EVERYTIME I turn the machine on (which is usually *at least* twice a day. Therefore I only have available approximately the last 3 days of logging.

Not good for spotting long term trends and doing analysis.

I have now manually switched to logrotate. It should be automatic.

---

### Post by svittal on 2009-04-21
> **hans.voss said:**
> This is most unfortunate for Ubuntu on laptops as the sysklod way of managing its log files creates a new file for me EVERYTIME I turn the machine on (which is usually *at least* twice a day. Therefore I only have available approximately the last 3 days of logging.

Not good for spotting long term trends and doing analysis.

I have now manually switched to logrotate. It should be automatic.


Could you please post the logrotates syslog you created?
Do you need to stop the syslogd before you let logrotate take care of syslog?
also if you use logrotate for syslog, what would be the replacement for all the stuff you have in syslog.conf?

---

### Post by cepal on 2011-11-14
you can get rid of the crontab logrotation of syslog by replacing old fashioned "sysklogd" package by a lot newer "**rsyslog**" (preferred by Debian) or "**syslog-ng**" (was quite popular in RedHat for some time but I would not recommend it, we faced some serious issues with syslog-ng).

Both, rsyslog and syslog-ng utilize the more modern logrotate way of rotating it's logs rather than the old sysklog way. But you may expect also more resources to be consumed (more features = more code = more memory used).

Cheers and sorry to participate in an old discussion, hope this might help to someone.

---

### Post by SeijiSensei on 2011-11-14
Current Ubuntu releases use rsyslog and /etc/logrotate.d/rsyslog.

---

### Post by cepal on 2011-11-14
> **SeijiSensei said:**
> Current Ubuntu releases use rsyslog and /etc/logrotate.d/rsyslog.

strange: I've got an openVZ VPS on bhost.co.uk where I chose ubuntu server 11.04 i386 image, it had sysklogd preinstalled and when I installed rsyslog, it is having some serious issues, utilizing CPU over 100% (4 cores) so there was probably a good reason to use sysklogd and it may have been one of the tweaks from default installation.

---

### Post by cepal on 2011-11-16
OK I found it in some other discussions; the problem is rsyslogd forks itself under "syslog" credentials and in the older kernel this user is not able to access kernel messages. Solution: comment line "$PrivDropToUser" in /etc/rsyslog.conf as I have very limited memory resources and can't afford two rsyslogd processes running as in the safer solution below.

There is another solution mentioned here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573980](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=573980)

for the case the comment of the article get's delete, here is cut and paste:

--------------- The rest is the cut'n'paste (with some formatting)  ---------------

**From:** "Stefan K." <archilles at kh-webcenter dot_de> [B]
To:[/B] 573980 at bugs dot debian dot_org 
**Subject:** Re: Bug#573980: rsyslog: klog does not work when dropping privileges [B]
Date:[/B] Wed, 08 Jun 2011 13:52:05 +0200

I´m using a simple workaround for some time now. In addition to the normal rsyslog instance I run a second one. The "main" rsyslog doesn´t fetch kernel messages anymore and therefore can drop its root privileges. But it´s now listening on localhost for them. 
```
$ModLoad imudp
$UDPServerAddress 127.0.0.1
$UDPServerRun 514
$AllowedSender UDP, 127.0.0.1
```The second instance runs as root and has only a minimum configuration to forward kernel messages to the "main" instance. So it is not reachable from the local network and opens no unix socket(?). 
```
$ModLoad imklog
*.* @127.0.0.1:514

/usr/sbin/rsyslogd -c5 -f /etc/rsyslog.conf.root -i /var/run/klogd-emu.pid
```It´s started after the "main" instance by adding it to /etc/init.d/rsyslogd and stopped by init on shutdown/reboot with SIGTERM. I expect this to be safer on a (exposed) server. Although this requires some additional resources (cpu power and main memory), I guess it should be negligible today :)

---

