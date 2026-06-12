---
title: "iptables logging showing up in dmesg but not in logfile"
date: 2016-02-02
forum: Server Platforms
---

### Post by sascha6 on 2016-02-02
Hello,

I'm trying since quiet a while getting the logging of iptables done. Even though i know already quiet a bite about ubuntu / linux, i would call myself still a newbe.

I do not get it to work to log iptables into a logfile...


What i did so far:

I have a test server running Ubuntu 14.04

I added this to my iptables:
iptables -A INPUT -j LOG --log-prefix "PORT DENIED: " --log-level 4

with iptables -vnL i can see the package counter increasing for this Rule.

I can see with dmesg all the time Rows like this:
[4106323.012664] PORT DENIED: IN=venet0 OUT= MAC= SRC=XX.XX.XXX.XX DST=XX.XXX.XXX.XXX LEN=104 TOS=0x00 PREC=0x00 TTL=121 ID=24136 DF PROTO=TCP SPT=63396 DPT=22 WINDOW=4006 RES=0x00 ACK PS URGP=0

So i would say my logging Rule of iptables is working and running...

I checked all the log files in /var/log/ for "PORT DENIED" but i could not find anything.

I really do not know what to do anymore...
If you want me to upload any config files, log files, or what ever, let me know and i will...

Thank you very much in advanced,
Sascha

---

### Post by darkod on 2016-02-02
Can you use something like this, adjusting it for your needs? [http://www.thegeekstuff.com/2012/08/iptables-log-packets/](http://www.thegeekstuff.com/2012/08/iptables-log-packets/)

It says by default the log entries would go to /var/log/messages so you should be able to find them there. But in that article there is also a way to create custom log file as destination.

---

