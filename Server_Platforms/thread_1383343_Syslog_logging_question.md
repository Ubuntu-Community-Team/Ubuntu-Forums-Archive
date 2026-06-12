---
title: "Syslog logging question"
date: 2010-01-17
forum: Server Platforms
---

### Post by remy06 on 2010-01-17
Hi all,

Currently Im having a syslog server that consolidate firewall logs on port 514 udp.

Im also having a IDS device that I wish to push its logs to this particular syslog server so that I can retrieve my IDS logs on this server as well.

Is it possible to do so?Having syslog listening on port 514 for both firewall and IDS logs?

If it is possible will the logs be recorded in a single log file?Or will it be recorded in a separate log file ie. firewall.log, IDS.log etc??

I wish to have them in separate individual log files or else there will be hard time segregating the log entries in a single file.

Can anyone advice on how to achieve this??

Thanks in advance.

---

### Post by remy06 on 2010-01-20
bump..

---

### Post by Lars Noodén on 2010-01-20
That depends.  Does the IDS log to syslog?  If so then, yes, you can log it also.  

Check the settings for *log facility* and *log level*.  See [syslog(3)](http://linux.die.net/man/3/syslog) for deatails.

The syslog facility code is usually used to sort the log file that the messages go to e.g. DAEMON, USER, AUTH, LOCAL0, LOCAL1, LOCAL2, LOCAL3, LOCAL4, LOCAL5, LOCAL6, LOCAL7.  

The syslog level categories the importance or nature of the message, to further help with sorting.  e.g. system is unusable, action must be taken immediately, critical conditions, error conditions, warning conditions, normal but significant condition, informational messages, and debugging  messages.

However, I'd be concerned about eavesdropping since if an intruder gets inside the LAN, he could then use the IDS for feedback on his status or success.  You could use a tunnel (TLS or SSH) to connect and then send the IDS messages over the tunnel.  You'd also want a watchdog to alert you if the tunnel is broken.

---

### Post by dnvikram on 2010-01-20
> **remy06 said:**
> Hi all,

Currently Im having a syslog server that consolidate firewall logs on port 514 udp.

Im also having a IDS device that I wish to push its logs to this particular syslog server so that I can retrieve my IDS logs on this server as well.

Is it possible to do so?Having syslog listening on port 514 for both firewall and IDS logs?

If it is possible will the logs be recorded in a single log file?Or will it be recorded in a separate log file ie. firewall.log, IDS.log etc??

I wish to have them in separate individual log files or else there will be hard time segregating the log entries in a single file.

Can anyone advice on how to achieve this??

Thanks in advance.

Try using SPLUNK...Its an awesome solution and have been using it since last 1year...and really easy checking syslogs for a particular server..it takes care of filtering and showing you the results you want..Its like you can search the logs for a specific pattern..

---

### Post by remy06 on 2010-01-21
Ic thanks for the info.

so local0 - local7 can be used to capture logs of other devices.

Will test it out and see how it goes.

---

### Post by fcefan00 on 2010-05-18
Hey,
I dont know what Ubuntu version you are using but since Debian 5.0(and becaus of this since Ubuntu 9.04?!?) rsyslog is the default syslog deamon. It's capable of Syslog over TCP, SSH and even complex Filtering. Tutorials are available on the homepage.

---

