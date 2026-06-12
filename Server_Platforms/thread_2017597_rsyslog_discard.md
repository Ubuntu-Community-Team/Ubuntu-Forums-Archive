---
title: "rsyslog discard"
date: 2012-07-05
forum: Server Platforms
---

### Post by palinurus on 2012-07-05
I am running 12.04 as home server / router. Hostapd is flooding syslog with wpa hand shake messages every 10 minutes, and making it difficult to see useful messages. 

I have the following code in my file 60-router.conf in rsyslog.d:

[CODE]
:programname, contains, "hostap"        -/var/log/hostapd.log
:programname, contains, "hostap"        ~

& ~
[/CODE
This successfully put the hostapd messages into /var/log/hostapd.log, but does not remove the hostapd stream from syslog. What am I doing wrong?

Following up on other bug reports of this nature, I have also tried commenting out "$RepeatedMsgReduction on" in rsyslog.conf, and "$RepeatedMsgReduction off". Neither change stops the hostapd stream to syslog

About to pull my hair out - or what's left of it. Some help please.

---

