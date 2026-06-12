---
title: "DNS statistics / How do I start dnsmasq with options every time?"
date: 2007-08-08
forum: Server Platforms
---

### Post by tillkowski on 2007-08-08
I only have a basic understanding of this, I'll try to be as clear as possible about my problem:

My server runs dnsmasq for DHCP and DNS services. I want to find out which domain name requests it receives from my local network.

The plan is this:
[LIST=1]
[*]Enable logging in /etc/dnsmasq.conf, this will make dnsmasq write pretty much everything to /var/log/syslog
[*]Specify a separate file to write the output to (Apparently this is possible by starting dnsmasq with the option --log-facility=[filename] )
[*]Do some cron / shell script / OOo magic
[*]See statistic of requested domains
[/LIST]

Currently I'm stuck at step 2. I know I can restart dnsmasq with the command ```
#/etc/init.d/dnsmasq restart
``` and I took a glimpse at the script (/etc/init.d/dnsmasq). I'm guessing there's an easy way to modify it to always start dnsmasq with an option, but I'm not sure how and I don't want to break anything.

Can somebody please help me out?

If anyone has a better idea of how to get  statistics, I'm open to suggestions. An account at OpenDNS doesn't work for me because my ISP doesn't give me a fix IP. I'm also reluctant to configure a full-blown DNS server because the configuration manual confused the hell out of me.

---

### Post by koenn on 2007-08-08
from to looks of it, adding
```
log-facility=/path/to/logfile
```to /etx/dnsmasq.conf should work. 

If it doesn't you might insert 
```
-- log-facility=/path/to/logfile \ 
``` in the start() section of the init script, above the "|| retrun 2 " line
```

start()
{
  [ .... ]
     
                -- log-facility=/path/to/logfile \ 
                || return 2
}

```
note the trailing  '\ '
it's important. 
and make a copy before you modify - then you have to worry lkeass about things breaking.

---

### Post by tillkowski on 2007-08-08
Thanks for the help, I really appreciate it.

Both methods work well in that they seem to successfully pass an argument to dnsmasq on startup.

However, I get get the following error message when i restart dnsmasq:
```
Restarting DNS forwarder and DHCP server: dnsmasqdnsmasq: bad log facility at line 393 of /etc/dnsmasq.conf
.
```

In the programmer's [dnsmasq changelog]("http://www.thekelleys.org.uk/dnsmasq/CHANGELOG") I found the following:
> 
release 2.39
            [...]
	    --log-facility can now take a file-name instead of a 
	    facility name.  [...]


Too bad the repositories only offer dnsmasq up to version 2.33.

Before I install dnsmasq from source :cry: can someone please tell me what a "log facility" is and whether it would make sense to create my own log facility for this purpose? (Googling the term didn't help much...)

---

### Post by koenn on 2007-08-09
I think "logging facility" refers to the fact that that you can have logs centralised on a remote host, a syslog server. That server (or the syslog daemon on it) would then be that logging facility. There's a mention in the syslogd man page that seems to indicate this. 
That would indicate that dnsmasq supports this sort of remote logging, but - as you found out - logging to a specified file is not supported until release 2.39.

---

### Post by tillkowski on 2007-08-10
I did some research:

There seem to be a limited number of logging facilities, LOCAL0, LOCAL1, ... LOCAL7.

dnsmasq uses LOCAL0 by default, so it seems to prefix all syslog messages by LOCAL0.[level] where [level] can be something like "error" or "info" or something.

Now all I had to do was go into /etc/syslog.conf and add the line:
```
local0.*               /var/log/dnsmasq.log
```
and restart syslog with 
```
/etc/init.d/sysklogd restart
```

Now all the output is being logged to /var/log/dnsmasq.log

A problem might be if another program uses the same logging facility - but it seems in that case i can change log-facility to USER and dnsmasq should prefix messages with dnsmasq.* (user name of the daemon)

Thinking about it, I should try to do this right now.

Edit: It doesn't work as expected, USER just prefixes every message with user.* and interferes with other log messages. I ended up using LOCAL6 just because it's probably not used yet.

---

