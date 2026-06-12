---
title: "Rsyslog configuration question/problem"
date: 2012-12-05
forum: Server Platforms
---

### Post by mainemojo on 2012-12-05
I am running the server version of Ubuntu 12.10 with rsyslogd 5.8.6.  I have a configuration file that reads:

[FONT=Courier New]$template LogFile, "/home/logs/%$YEAR%%$MONTH%/%$DAY%.log"
:fromhost, isequal, "system1.domain.com" ?LogFile
& ~
:fromhost, isequal, "system2.domain.com" ?LogFile
& ~
:fromhost, isequal, "system3.domain.com" ?LogFile
& ~[/FONT]

My log files are being created correctly.  The problem that I'm running into is that the "& ~" should stop the messages from being written to local files, but my /var/logs/rsyslog contains duplicates of every entry that goes into my "/home/logs/%$YEAR%%$MONTH%/%$DAY%.log".

Does anyone have any suggestions?  :confused:

---

### Post by koenn on 2012-12-05
> The problem that I'm running into is that the "& ~" should stop the messages from being written to local files, but my /var/logs/rsyslog contains duplicates of every entry that goes into my "/home/logs/%$YEAR%%$MONTH%/%$DAY%.log".


That would happen if you still have the default logging config (i.e "write to /var/logs/rsyslog") and they are seen (by rsyslogd) **before** your custom log & discard rules. 

The order in which logging rules are seen depends on their order in the rsyslog conf files, the alphabetical order of the files in the conf directory, and the place where conf directory gets included in the main conf file (i.e. the $IncludeConfig statement). 

So you should check if that is what causing the behavior you see. If it is, you can control it  by  eg. using numerals in the filenames in conf.d, like 0-mail, 99-misc_notices, or something. This makes the order of execution predictable, so it's easier to control what'll get logged where, and when to discard what.

---

### Post by mainemojo on 2012-12-06
Koenn, I think I understand what you're talking about.  I have my /etc/rsyslog.conf which ends with a '$IncludeConfig /etc/rsyslog.d/*.conf'.  In /etc/rsyslog.d, I have the default 20-ufw.conf and 50-default.conf along with my two custom conf files.

Based on your suggestion, I renamed system1.conf to 80-system1.conf and system2.conf to 90-system2.conf.  I got the same results.

I then changed 80-system1.conf to 30-system1.conf and 90-system2.conf to 31-system2.conf and that seems to have worked!  Thanks for the info!!!!

---

