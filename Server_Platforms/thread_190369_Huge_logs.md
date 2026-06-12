---
title: "Huge logs"
date: 2006-06-06
forum: Server Platforms
---

### Post by Rizado on 2006-06-06
I have a ubuntu computer running as a nat router with a pppoe connection to my isp. Everything works great and all but whenever I am connected to my isp I get huge logs. It's not really a problem other than that I can't use dmesg because of all the crap that's there.

```
[48471.337126] 'OUT-unknown:'IN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[48503.012383] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=61.230.5.15 DST=81.227.105.102 LEN=90 TOS=0x00 PREC=0x00 TTL=100 ID=31321 PROTO=UDP SPT=15870 DPT=64223 LEN=70
[48528.804506] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=219.111.201.174 DST=81.227.105.102 LEN=90 TOS=0x00 PREC=0xA0 TTL=107 ID=4923 PROTO=UDP SPT=6881 DPT=64223 LEN=70
[48645.268563] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=222.38.65.28 DST=81.227.105.102 LEN=126 TOS=0x00 PREC=0x00 TTL=96 ID=1033 PROTO=UDP SPT=22978 DPT=64223 LEN=106
[48708.110801] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=221.209.110.47 DST=81.227.105.102 LEN=485 TOS=0x00 PREC=0xA0 TTL=46 ID=0 DF PROTO=UDP SPT=35195 DPT=1026 LEN=465
[48771.337076] 'OUT-unknown:'IN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=258 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=238
[48771.337487] 'OUT-unknown:'IN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
[48802.431285] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=193.77.199.193 DST=81.227.105.102 LEN=90 TOS=0x00 PREC=0x00 TTL=116 ID=63112 PROTO=UDP SPT=8221 DPT=64223 LEN=70
[48832.002486] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=221.208.208.86 DST=81.227.105.102 LEN=483 TOS=0x00 PREC=0xC0 TTL=46 ID=0 DF PROTO=UDP SPT=48777 DPT=1027 LEN=463
[48964.557183] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=221.208.208.93 DST=81.227.105.102 LEN=485 TOS=0x00 PREC=0xA0 TTL=44 ID=0 DF PROTO=UDP SPT=35221 DPT=1026 LEN=465
[48964.559086] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=221.208.208.93 DST=81.227.105.102 LEN=485 TOS=0x00 PREC=0xA0 TTL=44 ID=0 DF PROTO=UDP SPT=35221 DPT=1027 LEN=465
[49021.144243] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=204.16.208.105 DST=81.227.105.102 LEN=449 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=49773 DPT=1026 LEN=429
[49021.146131] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=204.16.208.105 DST=81.227.105.102 LEN=449 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=49773 DPT=1027 LEN=429
[49047.066650] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=207.108.169.99 DST=81.227.105.102 LEN=90 TOS=0x00 PREC=0xC0 TTL=111 ID=43669 PROTO=UDP SPT=11728 DPT=64223 LEN=70
[49047.437411] ''IN-internet':'IN=ppp0 OUT= MAC= SRC=70.33.17.228 DST=81.227.105.102 LEN=90 TOS=0x00 PREC=0x00 TTL=108 ID=391 PROTO=UDP SPT=15995 DPT=64223 LEN=70
[49071.337127] 'OUT-unknown:'IN= OUT=eth1 SRC=192.168.0.1 DST=192.168.0.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58
```This is how it looks and it's allways like this but with different ips and other variations. What is it really? I've had it like this for almost two years. I read somewhere that it's common with unsolicited packages filling the logs, is this unsolicited packages? Can I disable it?

---

### Post by Rizado on 2007-01-01
And 7 months later I still have the same problem. Any ideas?

Sorry for bumping :-P

---

### Post by Biggus on 2007-01-14
How big is this file?

---

### Post by Rizado on 2007-03-10
ARGHHH I just dont get it! I just changed isp and hoped it would be better but oh no.

```
[2012439.430795] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=1281 DF PROTO=TCP SPT=56615 DPT=80 WINDOW=5080 RES=0x00 ACK FIN URGP=0
[2012439.494767] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=9781 DF PROTO=TCP SPT=56609 DPT=80 WINDOW=5804 RES=0x00 ACK FIN URGP=0
[2012440.858563] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=54852 DF PROTO=TCP SPT=56608 DPT=80 WINDOW=6528 RES=0x00 ACK FIN URGP=0
[2012457.091673] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=1282 DF PROTO=TCP SPT=56615 DPT=80 WINDOW=5080 RES=0x00 ACK FIN URGP=0
[2012457.155634] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=9782 DF PROTO=TCP SPT=56609 DPT=80 WINDOW=5804 RES=0x00 ACK FIN URGP=0
[2012459.927200] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=54853 DF PROTO=TCP SPT=56608 DPT=80 WINDOW=6528 RES=0x00 ACK FIN URGP=0
[2012492.409491] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=1283 DF PROTO=TCP SPT=56615 DPT=80 WINDOW=5080 RES=0x00 ACK FIN URGP=0
[2012492.473413] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=9783 DF PROTO=TCP SPT=56609 DPT=80 WINDOW=5804 RES=0x00 ACK FIN URGP=0
[2012498.060493] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=54854 DF PROTO=TCP SPT=56608 DPT=80 WINDOW=6528 RES=0x00 ACK FIN URGP=0
[2012558.869932] ''IN-internet':'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=71.139.6.35 DST=81.226.221.172 LEN=129 TOS=0x00 PREC=0x00 TTL=113 ID=2679 PROTO=UDP SPT=63512 DPT=57274 LEN=109
[2012563.053024] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=1284 DF PROTO=TCP SPT=56615 DPT=80 WINDOW=5080 RES=0x00 ACK FIN URGP=0
[2012563.116961] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=9784 DF PROTO=TCP SPT=56609 DPT=80 WINDOW=5804 RES=0x00 ACK FIN URGP=0
[2012566.531665] ''IN-internet':'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=71.139.6.35 DST=81.226.221.172 LEN=156 TOS=0x00 PREC=0x00 TTL=113 ID=3449 PROTO=UDP SPT=63512 DPT=57274 LEN=136
[2012574.331024] 'PASS-unknown:'IN=br0 OUT=eth1 SRC=192.168.0.2 DST=140.211.166.170 LEN=52 TOS=0x00 PREC=0x00 TTL=63 ID=54855 DF PROTO=TCP SPT=56608 DPT=80 WINDOW=6528 RES=0x00 ACK FIN URGP=0
[2012673.985885] 'IN-unknown:'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=190.16.104.20 DST=81.226.221.172 LEN=90 TOS=0x00 PREC=0x00 TTL=111 ID=9278 PROTO=UDP SPT=8805 DPT=28312 LEN=70
[2012806.019345] ''IN-internet':'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=60.24.77.157 DST=81.226.221.172 LEN=90 TOS=0x00 PREC=0x00 TTL=110 ID=9521 PROTO=UDP SPT=64973 DPT=17203 LEN=70
[2012810.088241] 'IN-unknown:'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=74.100.32.107 DST=81.226.221.172 LEN=90 TOS=0x00 PREC=0x00 TTL=112 ID=16054 PROTO=UDP SPT=9148 DPT=17203 LEN=70
[2012811.990527] ''IN-internet':'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=88.109.156.183 DST=81.226.221.172 LEN=90 TOS=0x00 PREC=0x00 TTL=115 ID=3951 PROTO=UDP SPT=14808 DPT=64629 LEN=70
[2012933.499452] ''IN-internet':'IN=eth1 OUT= MAC=00:50:fc:aa:76:18:00:0f:34:72:60:c0:08:00 SRC=140.112.94.57 DST=81.226.221.172 LEN=90 TOS=0x00 PREC=0x00 TTL=108 ID=16436 PROTO=UDP SPT=40791 DPT=28914 LEN=70
```I need to get this to stop, I can't use my logs!

---

### Post by Mr. C. on 2007-03-10
This is output from iptables going to syslog.  Either configure iptables to not log (not recommended), or change which logfile is being used for iptables logging.  Search for syslog in:

man iptables

MrC

---

### Post by Rizado on 2007-03-11
Well I've had some progress. Found this page:
[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)
Now I get all messages in /var/log/iptables.log, But also in kern.log and still in messages :( So now I get the same messages in three different logs.

EDIT: Add syslog to that list. Four different logs...

---

### Post by Mr. C. on 2007-03-11
Time to learn how syslog works:

```
man syslog.conf
```

and review Week 9 notes on Syslog: [http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

### Post by Rizado on 2007-03-19
I have read the man page now and think I've gotten a pretty good grip on it. Problem is, these messages are kernel info and that's what pretty much the rest of my log is too. If I put kern.info in another logfile I wont have any log left, and I'll be back to were I started.

I've also tried to put iptables to loglevel 4, which is supposed to only report warnings or higher but that doesn't work either, it just keep sending thoose information messages. For now I've set it to ULOG that I don't have so I wont get any messages at all. I'm going to check out ulogd now.

---

### Post by Mr. C. on 2007-03-19
You did restart/reload syslog and iptables, right ?

Right, you can't change the syslog facility for iptables.  It might be best to use a log parsing utility, so that you don't have to view the logs manually.

Try logwatch, for example.

MrC

---

