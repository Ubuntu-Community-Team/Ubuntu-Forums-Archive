---
title: "ufw is blocking some port 80 and should not"
date: 2011-04-15
forum: Security
---

### Post by hellz99 on 2011-04-15
First off, I have the default to deny all. The only rule I have in there is:
```

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
```

I verified that all other ports (ssh, mysql, etc) are getting blocked and I can hit 80 from home, work, several mobiles...works great.

For some reason I'm getting a bunch of UFW BLOCK lines like this:

```
Apr 15 11:28:54 serverX kernel: [UFW BLOCK] IN=eth0 OUT= MAC=XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX SRC=12.165.139.33  DST=XXX.XXX.XXX.XXX LEN=52 TOS=0x00 PREC=0x00 TTL=53 ID=37899    PROTO=TCP SPT=58696 DPT=80   WINDOW=65535 RES=0x00 ACK FIN     URGP=0 
```

I see DPT=80, meaning port 80 block. I've done whois on a bunch of ips getting blocked and it's everything from edu to mobiles to large businesses. I'm worried that these people are getting blocked from a few sites I'm running as virtual hosts.

Any reason why this is happening?
Also, does anyone know where I find docs to decode all of the other things in the ufw log (like SPT, WINDOW, RES, ACK, FIN, DF, SYN, URGP...etc)?


Thanks.

---

### Post by Doug S on 2011-04-15
Without the raw packets (i.e. from tcpdump or wireshark) it is hard to know for certain, so I am guessing a little. The packet is being blocked because the TCP syn bit is not set to indicate a new connection (other bits need to be reset also). Since the ACK and FIN bits are set this packet might be related to a previously closed tcp connection that the contrack table has since forgotten about. It is not unusual to have extra FIN packets and extra RST packets flying around, particulaly with the current use of CLOSE_WAIT at 60 seconds (it used to be much longer, and I always run it at 3600 seconds now). Myself, I find this subject of TCP conections quite complicated.
 
Specifically, your example packet is asking for the TCP session to be terminated via the ACK FIN bits. However there is no session, so the packet is being dropped. This is the correct action to take.
 
In the end, I do not think your are blocking people that are trying to properly access your web site. 
 
There are many good articles on internet about TCP and the flags bits and such.
The wiki one is good: [http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol) 
However, beware as there is also much erroneous information (as usual, I suppose).

---

### Post by bodhi.zazen on 2011-04-15
Well, you will need to do a bit of reading on TCP/IP protocols and if you understand those protocols the logs jargon is easy =)

[http://security.maruhn.com/](http://security.maruhn.com/)

[http://albanianwizard.org/tag/how-to-read-tcpdump-output](http://albanianwizard.org/tag/how-to-read-tcpdump-output)

---

### Post by bodhi.zazen on 2011-04-15
Here is another entry :

[http://www.rhyshaden.com/ipdgram.htm](http://www.rhyshaden.com/ipdgram.htm)

In terms of your rules and logs, hard to tell. From what you posted, your site works, so you are not dropping all traffic.

Those packets could be invalid, you would need to look further at the traffic, ie tcpdump , or write a set of logging rules to debug your rules.

---

### Post by hellz99 on 2011-04-15
thanks everyone for responses. 
Much help.

---

