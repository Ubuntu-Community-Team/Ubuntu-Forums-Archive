---
title: "Why is my server sending stuff to protected.hyperfilter.com"
date: 2015-05-08
forum: Server Platforms
---

### Post by Ron_Greve on 2015-05-08
Hi,

When looking into a problem with my email (my email seemed to come from my adsl modem instead of my local PC), I noticed when doing a 
```

tcpdump tcp port 25

```
I see (it sometimes takes a few minutes) the following traffic (and lots of it).
```

15:18:55.301508 IP protected.hyperfilter.com.48834 > ishprivate.informationsuperhighway.eu.smtp: Flags [S], seq 2724368804, win 8192, options [mss 1452,nop,wscale 8,nop,nop,sackOK], length 0
15:18:55.301537 IP ishprivate.informationsuperhighway.eu.smtp > protected.hyperfilter.com.48834: Flags [.], ack 1, win 29200, length 0
15:18:55.439762 IP protected.hyperfilter.com.48834 > ishprivate.informationsuperhighway.eu.smtp: Flags [S], seq 1407608794, win 8192, options [mss 1452,nop,wscale 8,nop,nop,sackOK], length 0
15:18:55.439791 IP ishprivate.informationsuperhighway.eu.smtp > protected.hyperfilter.com.48834: Flags [.], ack 1, win 29200, length 0
15:18:55.513565 IP protected.hyperfilter.com.34423 > ishprivate.informationsuperhighway.eu.smtp: Flags [S], seq 822784046, win 8192, options [mss 1452,nop,wscale 8,nop,nop,sackOK], length 0
15:18:55.513594 IP ishprivate.informationsuperhighway.eu.smtp > protected.hyperfilter.com.34423: Flags [.], ack 1, win 29200, length 0
15:18:55.577809 IP protected.hyperfilter.com.48834 > ishprivate.informationsuperhighway.eu.smtp: Flags [S], seq 690168044, win 8192, options [mss 1452,nop,wscale 8,nop,nop,sackOK], length 0
15:18:55.577839 IP ishprivate.informationsuperhighway.eu.smtp > protected.hyperfilter.com.48834: Flags [.], ack 1, win 29200, length 0
...

```
I use postfix/dovecot. My ubuntu version is:
```

NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"

```

Anyone got an idea what this is? The hyperfilter site seems to offer protection against ddos attacks. This seems almost like a dos attack itself :p.

Regards, Ron

EDIT:
Seems like they were actually initiating the connection. Dropped there traffic with [COLOR=black][FONT=monospace]iptables -I INPUT 1 -s 93.158.237.8 -j DROP. I now see it still incoming but at leas no outgoing anymore, saves me at least half the traffic [/FONT][/COLOR]:(

I sent them an email asking why they are actually sending me traffic.

---

### Post by slickymaster on 2015-05-08
Hi Ron_Greve, welcome to the forums.

I'm moving your thread to the **Server Platforms** sub-forum, which is the proper venue for it.

---

### Post by Doug S on 2015-05-08
Hi and welcome to Ubuntu forums.

There is always stuff like that going on.
Check your /var/log/mail.log and mail.err log files to be sure nothing bad is resulting.
Here is an excerpt from mine:```
May  8 15:53:35 doug-64 postfix/smtpd[8701]: connect from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 15:53:36 doug-64 postfix/smtpd[8701]: lost connection after AUTH from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 15:53:36 doug-64 postfix/smtpd[8701]: disconnect from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 15:56:56 doug-64 postfix/anvil[8707]: statistics: max connection rate 1/60s for (smtp:[COLOR=#ff0000]87.106.149.144[/COLOR]) at May  8 15:53:35
May  8 15:56:56 doug-64 postfix/anvil[8707]: statistics: max connection count 1 for (smtp:[COLOR=#ff0000]87.106.149.144[/COLOR]) at May  8 15:53:35
May  8 15:56:56 doug-64 postfix/anvil[8707]: statistics: max cache size 1 at May  8 15:53:35
May  8 15:58:41 doug-64 postfix/smtpd[8730]: connect from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 15:58:42 doug-64 postfix/smtpd[8730]: lost connection after AUTH from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 15:58:42 doug-64 postfix/smtpd[8730]: disconnect from s15436334.onlinehome-server.info[[COLOR=#ff0000]87.106.149.144[/COLOR]]
May  8 16:02:02 doug-64 postfix/anvil[8736]: statistics: max connection rate 1/60s for (smtp:[COLOR=#ff0000]87.106.149.144[/COLOR]) at May  8 15:58:41
May  8 16:02:02 doug-64 postfix/anvil[8736]: statistics: max connection count 1 for (smtp:[COLOR=#ff0000]87.106.149.144[/COLOR]) at May  8 15:58:41
May  8 16:02:02 doug-64 postfix/anvil[8736]: statistics: max cache size 1 at May  8 15:58:41
```However, in my case I have some firewall rules that will kick in after N attempts, so as to DROP packets from this jerk:```
May  8 16:03:50 doug-64 kernel: [6399245.123504] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=[COLOR=#ff0000]87.106.149.144[/COLOR] DST=173.180.XX.Y LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=17204 DF PROTO=TCP SPT=49995 DPT=25 WINDOW=8192 RES=0x00 SYN URGP=0
May  8 16:03:53 doug-64 kernel: [6399248.118787] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=[COLOR=#ff0000]87.106.149.144[/COLOR] DST=173.180.XX.Y LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=24358 DF PROTO=TCP SPT=49995 DPT=25 WINDOW=8192 RES=0x00 SYN URGP=0
May  8 16:03:55 doug-64 kernel: [6399250.195043] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=[COLOR=#ff0000]87.106.149.144[/COLOR] DST=173.180.XX.Y LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=29473 DF PROTO=TCP SPT=60947 DPT=25 WINDOW=8192 RES=0x00 SYN URGP=0
May  8 16:14:20 doug-64 kernel: [6399875.277270] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=[COLOR=#ff0000]87.106.149.144[/COLOR] DST=173.180.XX.Y LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=16708 DF PROTO=TCP SPT=63406 DPT=25 WINDOW=8192 RES=0x00 SYN URGP=0
May  8 16:14:23 doug-64 kernel: [6399878.361945] EMAIL BAD:IN=eth1 OUT= MAC=00:22:b0:75:c2:bd:6c:be:e9:a7:f1:07:08:00 SRC=[COLOR=#ff0000]87.106.149.144[/COLOR] DST=173.180.XX.Y LEN=52 TOS=0x00 PREC=0x00 TTL=118 ID=23641 DF PROTO=TCP SPT=63406 DPT=25 WINDOW=8192 RES=0x00 SYN URGP=0
```

EDIT: I had not seen your edit when I replied. Good for you on your direct DROP iptables rule, well done.

---

### Post by Ron_Greve on 2015-05-08
Hi Doug,

Thanks for your reply. 

Yes, I do occasionally check the mail.log to see if anything odd is going on. I have fail2ban installed which does an excellent job (I tighten the rules a bit). However what I found odd is that the traffic is not something that shows up in the mail.log (those I understand, lowlife's trying to spam/hack the system) but this doesn't seem to make much sense (unless they are trying to use the return traffic to test there systems, who knows :p).

Regards, Ron

---

### Post by Doug S on 2015-05-08
> **Ron_Greve said:**
> However what I found odd is that the traffic is not something that shows up in the mail.logOh. Your tcpdump excerpt does not show a completely established tcp session being created. I didn't know if it was just that what you posted was cropped or not. In the case where there is never a full TCP handshake completed, it might even be a forged return address.> **Ron_Greve said:**
> but this doesn't seem to make much sense (unless they are trying to use the return traffic to test there systems, who knows)Yes, there is lots of traffic that makes absolutely no sense at all. No apparent purpose, not even evil, just a waste of packets.

---

