---
title: "Remove some logs from messages"
date: 2011-01-03
forum: Server Platforms
---

### Post by malarie on 2011-01-03
Hi,

I have configured my Cisco ASa Firewall to send its logs to my ubuntu server in /var/log/cisco/

I see the logfiles populating in real time, but i can also see all the logs are also  wtitten to /var/log/messages.

How can i make sure i do not have a log redundancy?  I dont want my firewall logs displayed in messages since there are now sent to /var/log/cisco.

Thanks.

---

### Post by wongo888 on 2011-01-05
You would have to set up some rules in your rsyslogd configuration file. By default, all info, warn and notice severity entries (just about all) go to var/log/messages due to this line in /var/rsyslog.d/50-default.conf:

```
*.=info;*.=notice;*.=warn;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages
```

You would have to add a line like this (assuming router messages are going to a facility named local7):

```

local7.none;\
```

Severity 'none' means that you don't want to log anything from that facility. Your modified entry would look like this:

```
*.=info;*.=notice;*.=warn;\
	local7.none;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages
```

Check out the rsyslog.conf manual for syntax hints:

```
$ man rsyslog.conf
```

---

