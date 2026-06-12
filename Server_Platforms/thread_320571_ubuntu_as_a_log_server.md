---
title: "ubuntu as a log server"
date: 2006-12-17
forum: Server Platforms
---

### Post by ./redshift on 2006-12-17
Is anyone running ubuntu as a log server?

I have been searching the forums and the web looking for someone running ubuntu as a syslog server, but haven't really found any info yet...

I am now running Xubuntu Edgy on my main server, which will be a general use fileserver/log server/VM host and am trying to get the log server portion working.  I used to use SuSE so by force of habit I went to install syslog-ng, but upon selecting that, it wants to remove klogd and ubuntu-minimal, so I stopped that.

Now, klogd advertises itself as a kernel logging daemon, and there is a syslog.conf in /etc, so... is it configurable like syslog-ng or syslog to collect log messages from network devices and output to different files (I will be using it to collect the logs from all my cisco devices) or is there some way to get syslog installed and working?

Thanks,

---

### Post by ola on 2006-12-17
I'm very new to this but I managed to set up syslog as a remote logging service yesterday. 

This is what I did:

1). Set upp the other machine (a Linksys WRTG router running the Tomato Firmware) so it reports the logs to my logging server

2). Added the -r option to /etc/init.d/sysklogd (SYSLOGD="-r -u syslog"). This didn't work and I found out that there are another file (thanks to Jon for pointing that out!) /etc/default/syslogd that probably overrides the settings from the /etc/init.d/sysklogd. I don't know why, but it worked when I put the -r there as well.

3). I tried to set up so the logs from my router should be placed in an other file than /var/log/syslog but here is where I failed.. If you can figure that out please tell me!

Good luck! Best regards, 

Ola

---

### Post by ./redshift on 2006-12-18
Ola,

Thanks!  I will try that when I get home from work.  I will also try redirecting to different output files.  I have done this before with syslog-ng, but never with sysklog, so it might be different.  I will report back when I get it working.


Chris

---

### Post by chalex on 2006-12-18
The config file for syslog is /etc/syslog.  If you find out that you can't do what you want  with sysklog then you probably want to type "sudo apt-get install syslog-ng" then read the documentation in /usr/share/doc/syslog-ng.

---

### Post by ola on 2006-12-19
Yes, I heard about syslog-ng and I'll try that when I get my new computer!

Thanks a lot! Best regards,

Ola

---

### Post by frankabel on 2007-11-08
Hi,

On gusty:

 sudo apt-get install syslog-ng
[sudo] password for frankabel:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  klogd sysklogd ubuntu-minimal
The following NEW packages will be installed:
  syslog-ng
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 179kB of archives.
After unpacking 139kB of additional disk space will be used.
Do you want to continue [Y/n]? y

and all go fine. The syslog-ng is more powerfull and it replace completely the  klogd and sysklogd, even have a default configuration compatible with those packages.

Salute
Frank Abel

---

