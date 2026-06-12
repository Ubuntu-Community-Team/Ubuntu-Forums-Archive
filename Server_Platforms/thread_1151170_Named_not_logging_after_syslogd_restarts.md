---
title: "Named not logging after syslogd restarts?"
date: 2009-05-06
forum: Server Platforms
---

### Post by Sixsh00ter on 2009-05-06
Ubuntu ver 8.04.1 and Bind ver 9.4.2

I've set this up as a primary dns server, Bind is the only thing running on it, no gui, etc.  I followed the default settings so I have a named.conf, named.conf.options, and named.conf.local file. 

I have a log file I labeled as named.log in this path /var/log/bind.  I'm using logrotate to rotate out the file.

My problem is that after syslogd restarts in the morning. My named.log file don't start logging info until I restart Bind. The new named.log file gets created and the old files rotate out and compress. All of the other log files in /var/log, syslog, messages, mail, etc, rotate out and compress like they should, after syslogd restarts.

Anyone have a suggestion on how I can solve this problem?  I know that I could restart Bind using Cron but I shouldn't have to.

Below are snips of the files I'm using.

I named this one 'bind' and it's in the directory /etc/logrotate.d

/var/log/bind/named.log {
missingok
daily
create 644 bind bind
rotate 7
dateext
compress
}

// Beginning of Logging  named.conf.local

logging {

channel audit_log {
	file "/var/log/bind/named.log";
//	severity debug 3;
	print-time yes;

};
channel xfer_in_log {
	file "/var/log/xferin.log";
	severity debug 3;
	print-time yes;
};

channel xfer_out_log {
	file "/var/log/xferout.log";
	severity debug 3;
	print-time yes;
};

category security { audit_log; };
category config { audit_log; };
category resolver { audit_log; };
category xfer-in { xfer_in_log; };
category xfer-out { xfer_out_log; };
category notify { audit_log; };
category client { audit_log; };
category network { audit_log; };
category update { audit_log; };
category queries { audit_log; };
category lame-servers { null; };

// End of logging.
};

---

### Post by Sixsh00ter on 2009-05-11
I think I may have this sorted out.  Here's a link that explains it.
[http://www.usenet-forums.com/bind-users/235717-re-log-file-permssion-error.html](http://www.usenet-forums.com/bind-users/235717-re-log-file-permssion-error.html)

I reconfigured my setup to allow bind to do the logging rather than logrotate and restarted bind, and had this line in my syslog.
unable to rename log file '/var/log/bind/named.log' to '/var/log/bind/named.log.0': permission denied.

Turns out the user bind can't write to a directory owned by root.
I made bind the owner with full permissions to /var/log/bind/.  Seems to be working now, I'll know for sure in a day or two.

---

