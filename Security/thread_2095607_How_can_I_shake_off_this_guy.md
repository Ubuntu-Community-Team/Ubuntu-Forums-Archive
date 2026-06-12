---
title: "How can I shake off this guy ?"
date: 2012-12-17
forum: Security
---

### Post by leclerc65 on 2012-12-17
During the last few weeks someone from IP 88.191.127.22 tries to 'poke' thru my system at ports 3xxxx & 5xxxx, once or twice a day.
Is it part of the price to pay for surfing or should I worry ?
I even added, to no avail, this entry to /etc/hosts
127.0.0.1 faraway.pocentek.net
and that haven't stopped him at all.
I have to move all my 'sensitive' offline for now. My firewall is set to Deny In, Deny Out - ports opened only for standard stuff like DNS, HTTP, SMTP, Pop ...

---

### Post by CharlesA on 2012-12-17
The hosts file is only local to you and does nothing for someone trying to connect remotely.

As far as finding open ports in 3xxx and 5xxx, Remote desktop runs off port 3389 and VNC runs off 5900 and both of these are used for remote access. If you do not have either of these installed you should be fine.

Is this a desktop or server machine?

---

### Post by SeijiSensei on 2012-12-17
If you can alter your iptables rules, just block the host with a rule near the top of the ruleset like this:

```
/sbin/iptables -A INPUT -s 88.191.127.22 -j DENY
```

Then you'll never have to think about it again until someone tries a new IP address.  As Charles says, as long as you don't have open ports with services listening on them, there's nothing he can do except litter your iptables logs with rejections.

---

### Post by chadk5utc on 2012-12-17
Resolve Host: Paris, France  faraway.pocentek.net (88.191.127.22)
IP: 88.191.127.22, records: 2
medibuntu.org WHOIS
pocentek.net WHOIS
88.191.127.0 - 88.191.127.255
I also agree with the other post in addition you could block the whole range if it continues
iptables -A INPUT -p tcp -m iprange --src-range 88.191.127.0-88.191.127.255 -j DENY

---

### Post by chadk5utc on 2012-12-17
I would also suggest looking at fail2ban which does this for you
[http://www.fail2ban.org/wiki/index.php/Main_Page](http://www.fail2ban.org/wiki/index.php/Main_Page)
> sudo apt-get update
sudo apt-get install fail2ban

---

### Post by leclerc65 on 2012-12-17
> **CharlesA said:**
> 
As far as finding open ports in 3xxx and 5xxx, Remote desktop runs off port 3389 and VNC runs off 5900 and both of these are used for remote access. If you do not have either of these installed you should be fine.

Is this a desktop or server machine?
This is my desktop. I don't have these 2 ports opened.
I have seen a few, but the persistence of this guy really amazed me.
Thanks Charles and everybody, I can sleep now.

---

### Post by Hungry Man on 2012-12-17
I second Fail2Ban.

---

### Post by cprofitt on 2012-12-18
All the suggestions above are valid, but it might be worth investing in an inexpensive home router with a firewall on it too. Since this is a desktop there is likely no reason to expose it to the Internet directly.

---

### Post by iponeverything on 2012-12-18
> **leclerc65 said:**
> This is my desktop. I don't have these 2 ports opened.
I have seen a few, but the persistence of this guy really amazed me.
Thanks Charles and everybody, I can sleep now.

shouldn't be amazed as its probably not a person poking at keyboard, but rather a vulnerability scanner that is poorly configured..

---

### Post by 1clue on 2012-12-18
OK I have a couple suggestions.

First, fail2ban or similar.  Protect your computer from the inside, always.

Second, a cheap appliance router/firewall.  Defense in depth, and as long as you're careful they have a huge benefit because they just don't have much on them to exploit, which can be used to attack your network.

Third, something I can't really imagine why somebody else didn't say:  Contact your ISP.  If you're in the USA, then this sort of thing is illegal and the appropriate people will look into it if somebody complains.  I've done it 3 times now over the years with scans that were especially pesky, and they all stopped shortly after they were reported.  Whether it happened because my ISP put in a firewall rule of some sort, or somebody got a visit from law enforcement I don't know nor do I care.

I know it sounds ridiculous, you can't police the whole net right?  But as in real life, the cops can't come if they don't get a call.

---

### Post by leclerc65 on 2012-12-19
Thanks 1clue.
First I followed chadk5utc & Hungry Man and installed Fail2ban.
Up to the instruction

*sudo /etc/init.d/fail2ban restart*

I was greeted with the message
** Restarting authentication failure monitor fail2ban * 
So I gave up.:)
Then I followed cprofitt's advice and blocked that guy in my router's firewall.
If that doesn't work out then I will follow yours.
But learning is fun, despite my old age.:p
Happy holidays to all.

---

### Post by chadk5utc on 2012-12-19
Check your logs to get a better idea why fail2ban is giving errors we may be able to help you resolve them.
Try to run it and post the complete output from the Terminal here.

Something else you can do if you havent already is reconfigure ssh to another port out of the normal range maybe above 1029 this will also help then reconfigure your firewall to allow this and block the original(port22)

---

### Post by leclerc65 on 2012-12-19
I don't know how to "run" fail2ban , but here is the /var/log/fail2ban.log

```
2012-12-19 10:39:36,960 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 10:39:36,961 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 10:39:36,961 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2012-12-19 10:39:36,969 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 10:39:36,969 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 10:39:36,970 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 10:39:36,970 fail2ban.actions: INFO   Set banTime = 600
2012-12-19 10:39:36,991 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 11:01:38,667 fail2ban.server : INFO   Stopping all jails
2012-12-19 11:01:39,390 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 11:01:39,390 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 11:01:39,707 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 11:01:39,708 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 11:01:39,709 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
2012-12-19 11:01:39,768 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 11:01:39,768 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 11:01:39,768 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 11:01:39,769 fail2ban.actions: INFO   Set banTime = 86400
2012-12-19 11:01:39,790 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 11:09:27,084 fail2ban.server : INFO   Stopping all jails
2012-12-19 11:09:27,293 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 11:09:27,293 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 11:09:27,609 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 11:09:27,609 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 11:09:27,610 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
2012-12-19 11:09:27,618 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 11:09:27,618 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 11:09:27,618 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 11:09:27,619 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 11:09:27,640 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 11:16:28,191 fail2ban.server : INFO   Stopping all jails
2012-12-19 11:16:29,089 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 11:16:29,090 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 11:17:48,975 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 11:17:49,041 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 11:17:49,089 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
2012-12-19 11:17:49,550 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 11:17:49,683 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 11:17:49,683 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 11:17:49,683 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 11:17:49,705 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 11:33:58,296 fail2ban.server : INFO   Stopping all jails
2012-12-19 11:33:58,822 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 11:33:58,823 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 11:33:59,141 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 11:33:59,141 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 11:33:59,142 fail2ban.jail   : INFO   Jail 'ssh' uses Gamin
2012-12-19 11:33:59,150 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 11:33:59,150 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 11:33:59,151 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 11:33:59,151 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 11:33:59,172 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 12:13:04,413 fail2ban.server : INFO   Stopping all jails
2012-12-19 12:13:04,650 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 12:13:04,650 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 12:13:04,968 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 12:13:04,969 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 12:13:04,969 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2012-12-19 12:13:04,998 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 12:13:04,998 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 12:13:04,998 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 12:13:04,999 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 12:13:05,020 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 12:16:26,448 fail2ban.server : INFO   Stopping all jails
2012-12-19 12:16:27,242 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 12:16:27,242 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 12:16:27,560 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 12:16:27,560 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 12:16:27,560 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2012-12-19 12:16:27,568 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 12:16:27,568 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 12:16:27,568 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 12:16:27,569 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 12:16:27,590 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 12:42:44,695 fail2ban.server : INFO   Stopping all jails
2012-12-19 12:42:45,260 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 12:42:45,260 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 12:44:55,220 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 12:44:55,230 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 12:44:55,230 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2012-12-19 12:44:55,243 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 12:44:55,286 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 12:44:55,287 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 12:44:55,287 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 12:44:55,308 fail2ban.jail   : INFO   Jail 'ssh' started
2012-12-19 13:11:35,900 fail2ban.server : INFO   Stopping all jails
2012-12-19 13:11:36,493 fail2ban.jail   : INFO   Jail 'ssh' stopped
2012-12-19 13:11:36,493 fail2ban.server : INFO   Exiting Fail2ban
2012-12-19 13:11:36,810 fail2ban.server : INFO   Changed logging target to /var/log/fail2ban.log for Fail2ban v0.8.6
2012-12-19 13:11:36,811 fail2ban.jail   : INFO   Creating new jail 'ssh'
2012-12-19 13:11:36,811 fail2ban.jail   : INFO   Jail 'ssh' uses poller
2012-12-19 13:11:36,819 fail2ban.filter : INFO   Added logfile = /var/log/auth.log
2012-12-19 13:11:36,819 fail2ban.filter : INFO   Set maxRetry = 6
2012-12-19 13:11:36,819 fail2ban.filter : INFO   Set findtime = 600
2012-12-19 13:11:36,820 fail2ban.actions: INFO   Set banTime = 3600
2012-12-19 13:11:36,841 fail2ban.jail   : INFO   Jail 'ssh' started
```

---

### Post by 1clue on 2012-12-19
> **leclerc65 said:**
> Thanks 1clue.
...
But learning is fun, despite my old age.:p
Happy holidays to all.

In that case, when you get your basic hole fixed why don't you start reading up on your system logger and exactly how it works, including writing a few entries manually just to get familiar with it?

There's not a lot that's more important for security than good logging and a good system administrator who actually looks at them once in awhile.

Usually I assume the poster just wants to get up and going as soon as possible, but that really doesn't facilitate learning very well.

Obviously then you might want to read up on some networking topics, linux firewalls, SOHO router firewalls, ...

Good luck, have fun and take the time to really figure it out before you get distracted.

---

### Post by CharlesA on 2012-12-19
BTW, if you are wanting to keep an eye on logs without digging thru them, check out logwatch (it's in the repos).

---

### Post by chadk5utc on 2012-12-19
Ok I dont see anything in that output to indicate an issue, so try 
> sudo fail2ban-client status post the output also heres a link that may help check and copy config and tune it for your system.
[https://help.ubuntu.com/community/Fail2ban](https://help.ubuntu.com/community/Fail2ban)
or
[https://www.digitalocean.com/community/articles/how-to-protect-ssh-with-fail2ban-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-protect-ssh-with-fail2ban-on-ubuntu-12-04)

---

### Post by chadk5utc on 2012-12-19
+1 This is a great tool> **CharlesA said:**
> BTW, if you are wanting to keep an eye on logs without digging thru them, check out logwatch (it's in the repos).

---

### Post by leclerc65 on 2012-12-19
Here is the output of status

Status
|- Number of jail:	1
`- Jail list:		ssh

---

### Post by leclerc65 on 2012-12-19
[quote=1clue]
Obviously then you might want to read up on some networking topics, linux firewalls, SOHO router firewalls, ...

Good luck, have fun and take the time to really figure it out before you get distracted.[/quote]
I try, I try...
But at the age that when going upstairs to look for something, then forget what I am looking for, that doesn't help...:(

---

### Post by 1clue on 2012-12-19
> **leclerc65 said:**
> I try, I try...
But at the age that when going upstairs to look for something, then forget what I am looking for, that doesn't help...:(

Trust me.  I know ***EXACTLY*** what you mean.

---

### Post by hasinasi on 2013-05-19
I also recently found some events in my iptables logs coming from the very same IP address. The command "host" still says the corresponding IP address is "faraway.pocentek.net".
However, doing some googling, I found out that this IP also corresponds to "medibuntu.org", and a ```
host medibuntu.org
``` command confirmed this. I do have the medibuntu repos enabled, so I am thinking it's related to that. 

What I am puzzled about is which ports are actually being used. I am not an expert, but I am under the impression that "apt-get" only uses http. Therefore, port 80 should be open for outgoing traffic, which it is. I can update this machine (ubuntu repos), and I can browse the web. My log, however, shows **input** from this server 88.191.127.22 on port 80, whereas many different ports are listed for my machine (high port numbers). 

So how does this work? Obviously, the first IP request from my machine goes to the remote server (output), but then, the data has to flow from the server to my machine, which would be considered an input? Is this possibly related to the timing? Maybe, the server is responding too late, and then it is no longer considered a response but suddenly looks like an attack?

---

### Post by CharlesA on 2013-05-19
A a general rule of thumb, the destination port will be one of the known ports (80, 443, 22, 25, etc), and the source ports will be some random high numbered port. Without an example, it is hard to picture what you are talking about.

---

### Post by hasinasi on 2013-05-19
@CharlesA:

Thanks very much for your reply.
What you tell me is kind of what I expected. However, going through my browser logs, I often find entries where it is the other way round: the source being one of the known ports (often http or https) and the destination (incoming) being a high number. That's why I could not make sense of it. I see this stuff on several of my machines; much more frequently on machines that have web browsers running (not a real proof at this point).

Let me give you an example of my logs. The address 192.168.0.159 is the local address of my machine (behind a wireless router, which already block most of the mean stuff). The address 88.191.127.22 belongs to the machine that has previously been discussed in this thread. It appears to belong to "faraway.pocentek.net", but "medibuntu.org" also resolves to the same address, and therefore, it might be relevant to lots of ubuntu users. (I replaced the real MAC addresses with *** in the following code.)

```

May 19 05:02:11 haseee kernel: [76574.957701] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36759 SEQ=3895961960 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 05:02:12 haseee kernel: [76576.200122] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36766 SEQ=1289942439 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 05:02:12 haseee kernel: [76576.406922] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36767 SEQ=4155235900 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 05:02:12 haseee kernel: [76576.823143] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36769 SEQ=1498010674 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 05:02:13 haseee kernel: [76577.861990] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36774 SEQ=4167418617 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 05:02:14 haseee kernel: [76578.068836] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36775 SEQ=1631493983 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:39 haseee kernel: [86743.661530] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36848 SEQ=2177653835 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:39 haseee kernel: [86743.866111] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36849 SEQ=1542108056 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:41 haseee kernel: [86745.096420] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36855 SEQ=273139663 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:41 haseee kernel: [86745.312698] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36856 SEQ=3594443889 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:41 haseee kernel: [86745.723826] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36858 SEQ=3583800294 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 07:51:42 haseee kernel: [86746.347302] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36861 SEQ=299316482 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:02 haseee kernel: [92106.584708] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36914 SEQ=3939528884 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:03 haseee kernel: [92106.994400] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36916 SEQ=3172116063 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:03 haseee kernel: [92107.202958] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36917 SEQ=810468995 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:04 haseee kernel: [92108.024106] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36921 SEQ=1678517465 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:04 haseee kernel: [92108.232606] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36922 SEQ=1978130127 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:04 haseee kernel: [92108.445364] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36923 SEQ=4271162775 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:04 haseee kernel: [92108.648243] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36924 SEQ=2078825870 ACK=0 WINDOW=0 RES=0x00 RST URGP=0 
May 19 09:21:05 haseee kernel: [92109.262073] DROPPED IN=eth0 OUT= MAC=*** SRC=88.191.127.22 DST=192.168.0.159 LEN=40 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=TCP SPT=80 DPT=36927 SEQ=186303009 ACK=0 WINDOW=0 RES=0x00 RST URGP=0
```

Do you need any more info?

Thanks a bunch.
--hasi

---

### Post by CharlesA on 2013-05-19
That looks odd.. you don't usually see traffic from the source port of 80 (http) because a normal web server wouldn't be trying to connect to you in reverse.

This is what an attack should look like:

```
May 15 23:13:21 serenity kernel: [10100.497336] SSH Attack: IN=venet0 OUT= MAC= [COLOR="#FF0000"]SRC=173.45.97.98[/COLOR] [COLOR="#0000FF"]DST=xxx.xxx.xxx.xxx[/COLOR] LEN=60 TOS=0x00 PREC=0x00 TTL=51 ID=20821 DF PROTO=TCP [COLOR="#FF0000"]SPT=54244[/COLOR] [COLOR="#0000FF"]DPT=22[/COLOR] WINDOW=5840 RES=0x00 SYN URGP=0

```

---

### Post by sandyd on 2013-05-19
Have you set iptables to MIRROR by any chance.
It looks exactly what it should look like if MIRROR was enabled

---

### Post by Doug S on 2013-05-19
The log entries look O.K. to me, and just indicate that 88.191.127.22 is resetting the TCP session. The session might well have been started by the OP's computer. Linux uses a "half_duplex" close sequence, and it is very easy for one side to think the session has been closed while the other side doesn't, and thus a reset packet can be thought to be a whole new session packet, without a SYN. Here is an example from my logs, but notice that I use a different discriptor for each entry type to help me know where in the iptables the log entry came from:```
May 12 16:42:19 doug-64 kernel: [461050.935032] NEW TCP no SYN:IN=eth1 OUT= MAC=XX SRC=72.52.5.67 DST=XXX.XXX.XXX.XXX LEN=44 TOS=0x00 PREC=0x00 TTL=51 ID=44377 PROTO=TCP SPT=80 DPT=7315 WINDOW=1400 RES=0x00 ACK URGP=0
May 12 16:42:19 doug-64 kernel: [461051.349415] NEW TCP no SYN:IN=eth1 OUT= MAC=XX SRC=72.52.5.67 DST=XXX.XXX.XXX.XXX LEN=44 TOS=0x00 PREC=0x00 TTL=51 ID=44377 PROTO=TCP SPT=80 DPT=7315 WINDOW=1400 RES=0x00 ACK URGP=0
```If you want to know for certain, use tcpdump (or wireshark, if you prefer) and catch and entire TCP session or more.```
sudo tcpdump -n -nn -tttt -i eth0 host 88.191.127.22
```

---

### Post by hasinasi on 2013-05-19
@ sandyd: 
I don't have any MIRROR commands in my iptables.

---

### Post by hasinasi on 2013-05-19
@ Doug S:

Thank you so much for your thoughtful reply. It sounds quite plausible. It's good to know that there is a way to make sense of it. 
Interesting what you mention about the descriptors. Are those the sections in your log saying "NEW TCP no SYN:"?
How do you have to change iptables scripts to implement getting these descriptors in the logs? (I did a quick google search on "iptables descriptor", but nothing useful came up.)

Yes, I figured I have to dig deeper in order to figure out the problem in more detail (and understand more about TCP/IP, in general). I have never done any packet sniffing; and at this moment, I don't have the spare time to teach myself how to do it. Nevertheless, thanks for the hints (tcpdump), so that I can come back to it later :)

Best wishes, 
hasi

---

### Post by Doug S on 2013-05-19
Here are the corresponding lines of my iptables rules script:```
# V1.02: Many packets here are due to forgotten connections. Try REJECT instead of DROP.
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j LOG --log-prefix "NEW TCP no SYN:" --log-level info
#$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j DROP
$IPTABLES -A INPUT -p tcp ! --syn -m state --state NEW -j REJECT
```It turns out, that my example and my explaination above was not so great. I went back and extracted the actual packets and it turns out there was never a TCP session that got forgotten. Here is the tcpdump capture that led to the syslog entries of my earlier post:```
2013-05-12 16:42:19.581253 IP 72.52.5.67.80 > XXX.XXX.XXX.XXX.7315: Flags [.], ack 2636464277, win 1400, options [mss 512], length 0
2013-05-12 16:42:19.581350 IP XXX.XXX.XXX.XXX > 72.52.5.67: ICMP XXX.XXX.XXX.XXX tcp port 7315 unreachable, length 52
2013-05-12 16:42:19.995653 IP 72.52.5.67.80 > XXX.XXX.XXX.XXX.7315: Flags [.], ack 983077, win 1400, options [mss 512], length 0
2013-05-12 16:42:19.995709 IP XXX.XXX.XXX.XXX > 72.52.5.67: ICMP XXX.XXX.XXX.XXX tcp port 7315 unreachable, length 52
```So, in this case it was just some IP address, port 80 either trying stuff, or replying to an original packet to it with a forged return address (my address). Actually the RST isn't set, so I was mis-stating my example anyhow.

---

### Post by hasinasi on 2013-05-20
@Doug S:

Thanks so much!
I like the "--log-prefix" and "--log-level" additions. Makes logs much easier to analyze... I will implement these things on the next overhaul of my scripts. 

I just ran a "sudo apt-get update", which gave me three more iptables log events of the same kind. The update servers responded without out any noticeable delay, as I was watching the process in the terminal with several repositories responding per second. Why did this start now? I don't remember changing any settings, and in the past month the firewall logs were really quite. Suddenly I get these events, simply when the daily updates are run. The machine in question is running kubuntu 12.04.

I also found another interesting thing in the logs:
```

May 20 05:05:50 haseee kernel: [163194.895311] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36017 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK FIN URGP=0 OPT (0101080A026D650B82ED4B41)                                                                                                                                                                                                                       
May 20 05:05:51 haseee kernel: [163195.120194] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36018 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D654482ED4B41)                                                                                                                                                                                                                   
May 20 05:05:51 haseee kernel: [163195.576271] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36019 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D65B682ED4B41)                                                                                                                                                                                                                   
May 20 05:05:52 haseee kernel: [163196.488261] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36020 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D669A82ED4B41)                                                                                                                                                                                                                   
May 20 05:05:54 haseee kernel: [163198.316260] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36021 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D686382ED4B41)                                                                                                                                                                                                                   
May 20 05:05:57 haseee kernel: [163201.968251] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36022 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D6BF482ED4B41) 
May 20 05:06:05 haseee kernel: [163209.280283] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36023 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D731882ED4B41) 
May 20 05:06:19 haseee kernel: [163223.904266] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36024 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D816082ED4B41) 
May 20 05:06:49 haseee kernel: [163253.152267] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36025 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026D9DF082ED4B41) 
May 20 05:07:47 haseee kernel: [163311.584275] DROPPED IN= OUT=eth0 SRC=192.168.0.159 DST=91.189.91.14 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=36026 DF PROTO=TCP SPT=46243 DPT=80 SEQ=3658097242 ACK=3241237092 WINDOW=4538 RES=0x00 ACK PSH FIN URGP=0 OPT (0101080A026DD70082ED4B41) 

```
This is interesting, especially since **91.189.91.14** resolves to "**orobas.canonical.com**", so this must have been an automatic connection to an update server or so (if you go to orobas.canonical.com via browser, it looks like a repo). 
This appears to be the problem in reverse: if my machine is contacting the ubuntu update server via http, shouldn't the source port be 80 and the destination port a high number? The same machine has been running at least for a month without creating such events in the firewall logs. Automatic updating always worked well.

---

### Post by Doug S on 2013-05-20
> **hasinasi said:**
> This appears to be the problem in reverse: if my machine is contacting the ubuntu update server via http, shouldn't the source port be 80 and the destination port a high number?No. Your computer uses the high port number and earlier has opened a TCP session with port 80 of the destination. This is, perhaps, a similar problem to your earlier problem, but this time it is your end that is trying to finish a TCP session close, and not the other end. Your end keeps trying because the packets are being dropped instead of rejected, so your end does not know that the TCP connection has actually been terminated (I think). After a few re-tries it just gives up.

I do not have enough information to comment on the other parts of your post.

---

### Post by hasinasi on 2013-05-20
Interesting. Thank you!

Learning more about this, I am realizing that I am a little bit over my head in terms of how much I understand about TCP packets. 

I am bit surprised these packets end up being dropped, since I am using the following rule to allow http traffic, where "oAll" is my "catch-all" chain for outgoing traffic:
```

iptables -A oALL -p tcp  --dport 80  -m state --state NEW -j ACCEPT

```
I am using this in conjunction with another rule before that to allow all "related" traffic:
```
iptables  -A OUTPUT  -m state  --state ESTABLISHED,RELATED  -j ACCEPT
```

As expected, usual http browsing (and updating the computer via apt-get) is not a problem. So I am a bit puzzled why the above-mentioned events end up in the logs. 
Could these be invalid packets? I am not explicitly addressing packets of state "INVALID" (only NEW, ESTABLISHED, and RELATED), so they would be dropped and logged. 
I will modify my iptables such that invalid packets can be identified from the logs.

---

### Post by Doug S on 2013-05-20
The packets are not "NEW" nor are they "ESTABLISHED,RELATED", is why they get end up in the DROP rule.
What happens is (I think) the TCP session has been closed and the connection tracking table has forgotten about it, but the client application doesn't realize it. This happens a lot with the half-duplex close method and with various NAT type routers in the middle.

Going back a few posts, here is better example of a case where the other side is trying to reset a connection that my side has already thought of as closed (but not forgotten, in this example). First the logs entries:```
May 18 15:26:42 doug-64 kernel: [974914.165959] BAD80:IN=eth1 OUT= MAC=XX SRC=205.210.186.235 DST=XXX.XXX.XXX.XXX LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=54972 WINDOW=0 RES=0x00 RST URGP=0
May 18 15:26:42 doug-64 kernel: [974914.168128] BAD80:IN=eth1 OUT= MAC=XX SRC=205.210.186.235 DST=XXX.XXX.XXX.XXX LEN=40 TOS=0x00 PREC=0x00 TTL=57 ID=0 DF PROTO=TCP SPT=80 DPT=54972 WINDOW=0 RES=0x00 RST URGP=0
```And then the entire TCP session```
2013-05-18 15:26:41.741035 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [S], seq 4147817431, win 65535, options [mss 1460,nop,wscale 3,nop,nop,TS val 571005325 ecr 0,sackOK,eol], length 0
2013-05-18 15:26:41.793904 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [S.], seq 14144562, ack 4147817432, win 8000, options [mss 1460], length 0
2013-05-18 15:26:41.795412 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [.], ack 1, win 65535, length 0
2013-05-18 15:26:41.797641 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [P.], seq 1:1137, ack 1, win 65535, length 1136
2013-05-18 15:26:41.867327 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [.], ack 1137, win 16338, length 0
2013-05-18 15:26:42.675978 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [P.], seq 1:151, ack 1137, win 16338, length 150
2013-05-18 15:26:42.676185 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [F.], seq 151, ack 1137, win 16338, length 0
2013-05-18 15:26:42.676437 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [R.], seq 152, ack 1137, win 16338, length 0
2013-05-18 15:26:42.677949 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [.], ack 151, win 65535, length 0
2013-05-18 15:26:42.678376 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [F.], seq 1137, ack 151, win 65535, length 0
2013-05-18 15:26:42.678402 IP XXX.XXX.XXX.XXX.54972 > 205.210.186.235.80: Flags [F.], seq 1137, ack 152, win 65535, length 0
[COLOR=#ff0000]2013-05-18 15:26:42.812191 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [R], seq 14144713, win 0, length 0
2013-05-18 15:26:42.812262 IP XXX.XXX.XXX.XXX > 205.210.186.235: ICMP XXX.XXX.XXX.XXX tcp port 54972 unreachable, length 48
2013-05-18 15:26:42.814383 IP 205.210.186.235.80 > XXX.XXX.XXX.XXX.54972: Flags [R], seq 14144713, win 0, length 0
2013-05-18 15:26:42.814414 IP XXX.XXX.XXX.XXX > 205.210.186.235: ICMP XXX.XXX.XXX.XXX tcp port 54972 unreachable, length 48[/COLOR]
```My side did acknowledge the FIN request and the RST request, but the other side still tries to RST the connection, hence the logs entries. Here is the related section of my iptables:```
# At this point traffic to ports 80 or 443 is likely due to the half-duplex TCP close sequence. Be polite and REJECT instead of DROP.

$IPTABLES -A INPUT -i $EXTIF -p tcp -m multiport --sport 80,443 -j LOG --log-prefix "BAD80:" --log-level info
$IPTABLES -A INPUT -i $EXTIF -p tcp -m multiport --sport 80,443 -j REJECT

# Catch all rule, all other incoming is denied.
# (Leave the log-n-drop jump here so that in future I can remember how to do it.)
#
$IPTABLES -A INPUT -s $UNIVERSE -d $UNIVERSE -j log-n-drop
```

---

### Post by jeremywc on 2013-05-23
> **hasinasi said:**
> This appears to be the problem in reverse: if my machine is contacting the ubuntu update server via http, shouldn't the source port be 80 and the destination port a high number? The same machine has been running at least for a month without creating such events in the firewall logs. Automatic updating always worked well.

No, you've got a reverse understanding of how TCP/IP works. Their server has to listen on a static port and the default for HTTP is 80. If they were listening on something other than the default port, you'd have to manually specify it in your URL string (i.e. [http://www.example.com:8080](http://www.example.com:8080)). Your computer will randomly choose a port (usually something 50k+) that it will initiate it's connection FROM. Any packets coming back to you from the server will go to that random port.

EDIT: Doug beat me to it. Helps if I go to the end of the thread before replying. :-/

---

### Post by scruffyeagle on 2013-05-29
Hi! Much of this is over my head, but I did read all the posts... Anyway, I had a thought about this:

"medibuntu" sounds like it's some kind of medical program. However, checking in Synaptic, it didn't show up for this Xubuntu v12.04 OS. (3rd-party source?) What I was thinking, is that if this is a program you have installed on your machine, a remote server might be trying to provide data updates without realizing you don't have the program in operation at the moment; i.e., if the program had been running at that moment, then it would have gathered the data in an authorized manner, and no firewall probe event would have been reported.

Just a thought...

---

### Post by cariboo on 2013-05-30
> **scruffyeagle said:**
> Hi! Much of this is over my head, but I did read all the posts... Anyway, I had a thought about this:

"medibuntu" sounds like it's some kind of medical program. However, checking in Synaptic, it didn't show up for this Xubuntu v12.04 OS. (3rd-party source?) What I was thinking, is that if this is a program you have installed on your machine, a remote server might be trying to provide data updates without realizing you don't have the program in operation at the moment; i.e., if the program had been running at that moment, then it would have gathered the data in an authorized manner, and no firewall probe event would have been reported.

Just a thought...

Medibuntu is an unofficial repository for media codecs that aren't included in the main Ubuntu repositories, it's been around for almost as long as Ubuntu itself. It looks like the bad guy may be spoofing the Medibuntu ip address.

---

### Post by scruffyeagle on 2013-06-10
Got it.  Naughty, naughty.  Somebody ought to spank his modem.

---

### Post by hasinasi on 2013-06-10
@cariboo907:
I don't think it's IP spoofing, as I only get errors in my log as long as medibuntu is enabled as a repository. The occurrence of the problem in my logs also coincides with running "apt-get update". Therefore it (reproducibly) only happens when my machine establishes contact with the repos and not due to an action from an outside person.

---

### Post by scruffyeagle on 2013-06-13
Is it possible for a hacker to monitor the medibuntu activity, and spoof to try to take over or exploit the connection for their own purposes?

---

### Post by CharlesA on 2013-06-13
I guess they could be monitoring the repo, but that is why the packages are signed with GPG keys...

---

