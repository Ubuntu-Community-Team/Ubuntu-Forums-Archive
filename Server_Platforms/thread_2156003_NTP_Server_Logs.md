---
title: "NTP Server Logs"
date: 2013-06-20
forum: Server Platforms
---

### Post by hiboujid on 2013-06-20
Hi,
i am using a Ubuntu Server as a NTP Server, it's working very well, the clock is synchronised.
now i am trying to activate Logs so i can see "Clients" that synchronize with my server.

i added two lines to my config :
---------------------------
logfile /var/log/ntpd.log
statsdir /var/log/ntpstats/
---------------------------

the second one : "statsdir" give informations just about external servers with whom my server synchronize it's clock, it's not the informations i am seeking

even after restarting my daemon, when i check the "/var/log" directory i cannot find the file ntpd.log, i wonder why ?
is it the correct line to add to activate logs ?
such file /var/log/ntpd.log, will it contain informations about NTP clients ?

Thank you so much

---

### Post by SeijiSensei on 2013-06-20
By default ntpd will log to /var/log/syslog.  Unless you need to route the NTP entries to a separate file, just use the default.  You can always extract the ntpd entries with "grep ntp /var/log/syslog".

---

### Post by hiboujid on 2013-06-20
thanks for your reply, however it doesnt work

i synchronized 2 servers (A & B) with my NTP server successfully, then i entered the command " cat /var/log/syslog | grep @IP-Srv-A/B" and i got nothing displayed

same thing with " cat /var/log/syslog | grep ntp" there is some ntpd entries like "Jun 20 12:14:56 srvntp ntpd[40621]:......" but no trace about the NTP clients

my main goal is having the list of all the NTP clients that synchronize with my server

any hint ?

Thanks

---

### Post by SeijiSensei on 2013-06-20
You can log the requests with iptables:

```
/sbin/iptables -A INPUT -p udp --dport 123 -j LOG
```

---

### Post by hiboujid on 2013-06-21
Thanks a lot

now i can see the entries in syslog "cat syslog | grep DPT=123"
but the logs are firewall logs, there is no indication about what have been done in NTP, the synchronization is it ok ? any error ? difference between the 2 clocks ....

so it's basically just a way to be sure that the client has contacted the server, nothing else.
well, it's a significant information, but is there anyway to have more details ?

I apologize for the inconvenience

Thanks

---

### Post by Lars Noodén on 2013-06-21
Syslog will give you the most details.  

You can use grep directly on the logs to look for ntpd activity such as synchronization:

```

grep ntpd /var/log/syslog
grep ntpd /var/log/syslog.1

```

That use of grep will get any lines that even mention ntpd, such as use of apparmor, and things with the string 'ntpd' like ntpdate

---

### Post by hiboujid on 2013-06-21
sorry but there is no information about the NTP clients in the syslog
just some information about the daemon nothing else

---

### Post by Lars Noodén on 2013-06-21
Did you also look in the previous log, /var/log/syslog.1 ?  If syslog is very fresh there might not be ntpd data in it.

---

### Post by hiboujid on 2013-06-21
yes done it, but still no results

in addition before each check on the logs i try to resynchronize my servers to be sure that there is a communication to be logged

it appear that the log of the NTP server contain just information about the daemon, the NTP server doens't log entries about NTP clients

is there any expert here to confirm this observation ?

Thanks

---

### Post by SeijiSensei on 2013-06-21
Yes, it only logs daemon activity.  (Perhaps you are not seeing the results in the log because you still have the logfile setting in ntp.conf?)  To see the clients use the iptables rule I gave you above.

---

### Post by hiboujid on 2013-06-21
i deleted the lines added to ntp.conf once i got your answer (iptables)

however the problem is still the same :

i can see the entries about the firewall rule in syslog but there is no indication about what have been done in NTP, the synchronization is it ok ? any error ? difference between the 2 clocks ....

---

### Post by SeijiSensei on 2013-06-21
ntpd never logs things like that.  You can look at the client to see if the client successfully synchronized with the server.  Why would think it is not working?  I've used ntpd for years, and it is very reliable.  It is pretty much a "set-it-and-forget-it" type of daemon.

---

### Post by hiboujid on 2013-06-22
Ok thanks

we have a  lot of DMZs, lot of PCs, Servers, we wanted to have a single log file to search for anomalies in NTP protocol

i agree that in general it's a "set-it-and-forget-it" but sometimes there is some equipements with the wrong date that cannot synchronize their clock (example bios pb, ...), there is also some equipements that cannot synchronize their clock if the difference betwenn the 2 clocks is big even if they have the correct date.

so it's about a centralized view for troubleshooting.

Thanks

---

### Post by Lars Noodén on 2013-06-22
If you want centralized logging, you can have the clients running ntpd forward part of their syslog activity to a central server.  Take a look at the manual page for rsyslogd and for [rsyslog.conf](http://manpages.ubuntu.com/manpages/quantal/en/man5/rsyslog.conf.5.html) and look for the material on remote forwarding.  Unfortunately there does not seem to be an obvious way to have ntpd log to a customized log facility (e.g. local0).  That would make it easier to sort.  The package logwatch on the central log server might help.

---

### Post by SeijiSensei on 2013-06-22
I looked at the source code for ntpd.  It looks like you could alter the file [ntp-source-root]/lib/isc/log.c to change the name of facility being used.  I'm not a C programmer, but if you have any around, ask them to take a look at the source.

Current release version: [http://www.eecis.udel.edu/~ntp/ntp_spool/ntp4/ntp-4.2/ntp-4.2.6p5.tar.gz](http://www.eecis.udel.edu/~ntp/ntp_spool/ntp4/ntp-4.2/ntp-4.2.6p5.tar.gz)

---

### Post by koenn on 2013-06-22
> **Lars Noodén said:**
>  Unfortunately there does not seem to be an obvious way to have ntpd log to a customized log facility (e.g. local0).  That would make it easier to sort.  
rsyslog has a pretty advanced filtering mechanism (host, originating program, specific strings occuring in the log message, ...) so  it's probably doable to filter out 'ntp' log entries and direct them to a dedicated log

---

### Post by Lars Noodén on 2013-06-23
> **koenn said:**
> rsyslog has a pretty advanced filtering mechanism (host, originating program, specific strings occuring in the log message, ...) so  it's probably doable to filter out 'ntp' log entries and direct them to a dedicated log

The manual page for rsyslog.conf doesn't give much help with examples or clarification.  There is the [online documentation for rsyslogd](http://www.rsyslog.com/doc/manual.html) but it could also be made more clear.  I guess the place to start would be here: 

[http://www.rsyslog.com/doc/property_replacer.html](http://www.rsyslog.com/doc/property_replacer.html)

---

### Post by koenn on 2013-06-23
> **Lars Noodén said:**
> The manual page for rsyslog.conf doesn't give much help with examples or clarification.  There is the [online documentation for rsyslogd](http://www.rsyslog.com/doc/manual.html) but it could also be made more clear.  
True, and sometimes it's even more confusing when the documentation describes features that are not yet available in the version ubuntu or debian are using.

FWIW, I wrote down some reminders when i first tackled (centralized) ligging with rsyslog : [ http://users.telenet.be/mydotcom/howto/linux/syslogserver.html]("http://users.telenet.be/mydotcom/howto/linux/syslogserver.html")

---

### Post by gordon4 on 2014-05-07
> **hiboujid said:**
> i deleted the lines added to ntp.conf once i got your answer (iptables)

however the problem is still the same :

i can see the entries about the firewall rule in syslog but there is no indication about what have been done in NTP, the synchronization is it ok ? any error ? difference between the 2 clocks ....





Ahhhhhh .....hiboujid ntp traffic is UDP traffic, you don't have too much to see there.

You need to check this information from the client, try 'ntpq -p', 'ntptrace' commands or see the log file of client.

---

