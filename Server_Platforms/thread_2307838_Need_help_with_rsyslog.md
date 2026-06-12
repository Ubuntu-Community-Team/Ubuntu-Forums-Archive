---
title: "Need help with rsyslog"
date: 2015-12-28
forum: Server Platforms
---

### Post by genka on 2015-12-28
I'm trying to do few extra things with rsyslog and can't get anything beyond the basic logging to work. I need to add two functions: receive remote logs and forward logs to a local application.

Receiving the remote logs seems to be easy, just uncomment two line in rsyslog.conf. I did that, but nothing remote is logged. I ran tcpdump and could see the incoming messages on udp 514. Than I ran rsyslog -d from the console and enabled debugging in rsyslog.conf
When I send a syslog message from a remote host, I'm getting this debug:
```
2035.806958321:7fc2c54a6700: imudp: epoll_wait() returned with 1 fds
2035.807111034:7fc2c54a6700: imudp:recv(6,55),acl:1,msg:<13>Dec 29 01:20:35 raspberrypi gt: this is only a testfrom UDP: [10.0.0.11]:53246->[10.0.0.4]:16155" x-info="http://www.rsyslog.com"] start
2035.807188590:7fc2c54a6700: msg parser: flags 70, from '~NOTRESOLVED~', msg '<13>Dec 29 01:20:35 raspberrypi gt: this is only a test'
2035.807233068:7fc2c54a6700: parse using parser list 0xfc90e0 (the default list).
2035.807262747:7fc2c54a6700: Parser 'rsyslog.rfc5424' returned -2160
2035.807288185:7fc2c54a6700: Message will now be parsed by the legacy syslog parser (one size fits all... ;)).
2035.807317664:7fc2c54a6700: Parser 'rsyslog.rfc3164' returned 0
2035.807351262:7fc2c54a6700: msg repeated 2 times
```

I can't figure if this is debug shows a problem

My second function is to send the logging data to Observium, which I did according to the instructions at [http://observium.org/w/Rsyslog_Syslog_Server](http://observium.org/w/Rsyslog_Syslog_Server)
Basically I needed to add a file to /etc/rsyslog.d folder with this text:

```
$template observium,"%fromhost%||%syslogfacility%||%syslogpriority%||%syslogseverity%||%syslogtag%||%$year%-%$month%-%$day% %timereported:8:25%||%msg%||%programname%\n" 
$ModLoad omprog $ActionOMProgBinary /opt/observium/syslog.php 
 :inputname, isequal, "imudp" :omprog:;observium
 & stop
```
Logging of the local data files in /var/log works fine, but nothing is passed to Observium

I went as fat as purging and reinstalling rsyslogd, but couldn't make these two functions work.

---

### Post by matt_symes on 2015-12-28
Thread moved to **Server Platforms**

You may get better help for your query in this forum.

---

