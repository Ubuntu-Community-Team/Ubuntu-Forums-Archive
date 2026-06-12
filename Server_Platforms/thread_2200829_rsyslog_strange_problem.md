---
title: "rsyslog strange problem"
date: 2014-01-21
forum: Server Platforms
---

### Post by alzyx on 2014-01-21
1st of all I apologize: I'm running Fedora (F19) - but I saw a lot of helpful answers about rsyslog on this forum and I come here hat in hand for some guidance...

I am tired of seeing my /var/log/messages full of info coming from avahi-daemon: stuff like:
```
Jan 21 14:13:42 localhost avahi-daemon[554]: Invalid response packet from host 10.10.22.3.
```
from my local network

...so I thought about disabling the reporting modifying /etc/rsyslog.conf.

I modified this line:
```
*.info;mail.none;authpriv.none;cron.none   /var/log/messages
```

to this line
```
*.info;mail.none;authpriv.none;cron.none;avahi-daemon.none   /var/log/messages
```

but with the new line rsyslog seems not working: *systemctl restart rsyslog* reports it as running, but nothing gets ever written in *messages*


There is some problem in the way I modified that line?

thank you!

---

### Post by tgalati4 on 2014-01-21
My understanding is that rsyslog normally sends messages to /var/log/syslog of the host (receiving) system.  /var/log/messages are probably locally-generated.  Perhaps configure [avahi-daemon]("http://manpages.ubuntu.com/manpages/precise/en/man5/avahi-daemon.conf.5.html") to ignore the IP address.

---

### Post by SeijiSensei on 2014-01-21
Syslog messages are routed by "[facilities]("http://wiki.gentoo.org/wiki/Rsyslog#Facility")."  I suspect avahi-daemon just uses the daemon facility.  Changing the settings for that would also change where other daemons are logged.

If avahi-daemon allows you to change the facility, you can set it to use one of the seven user-defined "local" facilities and route traffic for that to a separate log file or /dev/null in rsyslog.conf.

---

### Post by alzyx on 2014-01-22
thank for your help, I'll look for details about avahi-daemon.
Anyway you don't find any problem in my rsyslog.conf line? Because in any case I find it strange that rsyslog stops working

---

### Post by SeijiSensei on 2014-01-22
> **tgalati4 said:**
> My understanding is that rsyslog normally sends messages to /var/log/syslog of the host (receiving) system.  /var/log/messages are probably locally-generated.

He's running Fedora. RedHat-flavored distros use /var/log/messages as the destination for log entries that would be written to /var/log/syslog on Debian-flavored systems like Ubuntu.

> **alzyx said:**
> thank for your help, I'll look for details about avahi-daemon.
Anyway you don't find any problem in my rsyslog.conf line? Because in any case I find it strange that rsyslog stops working

Are you saying that nothing is now being written to /var/log/messages?  Are you running other daemons on this box? On my CentOS servers, /var/log/messages contains entries from daemon services like xinetd, clamd, openvpn and named.  On desktop machines there shouldn't be very many processes that write to this log file.

---

### Post by alzyx on 2014-01-22
> **SeijiSensei said:**
> Are you saying that nothing is now being written to /var/log/messages?  Are you running other daemons on this box? On my CentOS servers, /var/log/messages contains entries from daemon services like xinetd, clamd, openvpn and named.  On desktop machines there shouldn't be very many processes that write to this log file.

exactly - nothing is written anymore and I'm sure rsyslog is stuck in some way. Though it is reported as running, if I stop&restart some process (e.g. systemctl restart cups) nothing gets reported.
If I restore the rsyslog.conf file, the restart of cups gets reported.

So in some way that apparently harmless line is not so harmless after all!

---

### Post by alzyx on 2014-01-23
ok, so I discovered that rsyslog's syntax is rather complex, but some help can be found at [http://www.rsyslog.com/doc/rsyslog_conf_filter.html](http://www.rsyslog.com/doc/rsyslog_conf_filter.html) and [http://www.rsyslog.com/tag/some-core-recipies/](http://www.rsyslog.com/tag/some-core-recipies/)
So if you want to filter out and not log a message from a service named avahi-daemon, insert this line (before the line *.info;mail.none;authpriv.none;cron.none   /var/log/messages)
:syslogtag, contains, "avahi-daemon" ~

or, to filter out a message containing the string xxx:
:msg, contains, "xxx" ~

---

### Post by tgalati4 on 2014-01-23
Thanks for sharing those helpful links.

---

### Post by koenn on 2014-01-23
> **alzyx said:**
> I'm running Fedora  - [...]  and I come here hat in hand ... 
lol.

> 
I modified this line:
to this line
```
*.info;mail.none;authpriv.none;cron.none;avahi-daemon.none   /var/log/messages
```


change it back to what it was;
mail, authpriv,cron, ... in that line are syslog facilities, not names of daemons/processes. By adding "avahi-daemon" (not a facility label) you've created an invalid config - that's probably the reason your logging stopped working.




as for filtering whit rsyslog : the link provided by alzyx is a good starting place, rsyslog has quite powerful filtering mechanisms.
however, it's probably best to first see if you can reduce or turn of avahi logging.  For most services the log-level is configurable, but I don't know how that is for avahi.

---

