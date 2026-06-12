---
title: "Attempt to intrude laptop?"
date: 2010-04-22
forum: Security
---

### Post by nightwolf2k5 on 2010-04-22
Hi there,

I recently put my ubuntu laptop on DMZ on my router.. I fell asleep and woke up to find a remote desktop sharing request!
This morning, I went ahead and got myself the firestarter firewall and left my comp on to see what happens.
Over the day, it has blocked quite a few events. It sparked my curiosity and I did a traceroute to one of the IP's that featured quite a bit: 221.192.199.48

Turns out, its from china.. A whois request on this ip gave me this:
```
% [whois.apnic.net node-2]
% Whois data copyright terms    http://www.apnic.net/db/dbcopyright.html

inetnum:      221.192.0.0 - 221.195.255.255
netname:      UNICOM-HE
descr:        China Unicom Hebei Province Network
descr:        China Unicom
country:      CN
admin-c:      CH1302-AP
tech-c:       KL984-AP
remarks:      service provider
mnt-by:       APNIC-HM
mnt-lower:    MAINT-CNCGROUP-HE
mnt-routes:   MAINT-CNCGROUP-RR
status:       ALLOCATED PORTABLE
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
remarks:      This object can only be updated by APNIC hostmasters.
remarks:      To update this object, please contact APNIC
remarks:      hostmasters and include your organisation's account
remarks:      name in the subject line.
remarks:      -+-+-+-+-+-+-+-+-+-+-+-++-+-+-+-+-+-+-+-+-+-+-+-+-+-+
changed:      hm-changed@apnic.net 20040329
changed:      hm-changed@apnic.net 20060124
changed:      hm-changed@apnic.net 20060125
changed:      hm-changed@apnic.net 20080314
changed:      hm-changed@apnic.net 20090508
source:       APNIC

route:        221.192.0.0/14
descr:        CNC Group CHINA169 Hebei Province Network
country:      CN
origin:       AS4837
mnt-by:       MAINT-CNCGROUP-RR
changed:      abuse@cnc-noc.net 20060118
source:       APNIC

person:       ChinaUnicom Hostmaster
nic-hdl:      CH1302-AP
e-mail:       abuse@chinaunicom.cn
address:      No.21,Jin-Rong Street
address:      Beijing,100140
address:      P.R.China
phone:        +86-10-66259940
fax-no:       +86-10-66259764
country:      CN
changed:      abuse@chinaunicom.cn 20090408
mnt-by:       MAINT-CNCGROUP
source:       APNIC

person:       Kong Lingfei
nic-hdl:      KL984-AP
e-mail:       konglf5@chinaunicom.cn
address:      45, Guang An Street, Shi Jiazhuang City, HeBei Province,050011,CN
phone:        +86-311-86681601
fax-no:       +86-311-86689210
country:      cn
changed:      konglf5@chinaunicom.cn 20090206
mnt-by:       MAINT-CNCGROUP-HE
source:       APNIC



```
I know I am probably being highly paranoid, but I figured I might as well ask the community their opinion.
How safe am I being on Ubuntu?

---

### Post by cariboo on 2010-04-22
You'd be much safer if you turned off remote desktop sharing, and used ssh to access the desktop remotely.

---

### Post by cdenley on 2010-04-22
You're safe until you go installing/enabling servers such as VNC (remote destkop) and allowing access to them from the internet. If you didn't require the local user to allow that session request, your system would have been compromised. Your system is safe until you do something to make it unsafe.

The internet is full of people/bots checking random IP's for servers such as VNC which are often not secured properly. I get a few people trying to guess a password on my FTP server every week.

---

### Post by bodhi.zazen on 2010-04-22
> **nightwolf2k5 said:**
> Hi there,

I recently put my ubuntu laptop on DMZ on my router.. I fell asleep and woke up to find a remote desktop sharing request!
This morning, I went ahead and got myself the firestarter firewall and left my comp on to see what happens.
Over the day, it has blocked quite a few events. It sparked my curiosity and I did a traceroute to one of the IP's that featured quite a bit: 221.192.199.48

Turns out, its from china.

Well, the ipaddress is from china but I would not assume that that is the actual ipaddress of the attempted inturder.

Nothing like reading the logs to instill some healthy paranoia.

1. I advise you do not use VNC. Use ssh -X , forward VNC over ssh, or use Freenx.

2. If you install a server, VNC, ssh, or otherwise, be sure to learn how to secure it.

---

### Post by cdenley on 2010-04-22
> **bodhi.zazen said:**
> Well, the ipaddress is from china but I would not assume that that is the actual ipaddress of the attempted inturder.


You can usually make a pretty good guess with a port scan.
```

cdenley@ubuntu:~$ sudo nmap -sV -O 221.192.199.48

Starting Nmap 5.00 ( http://nmap.org ) at 2010-04-22 15:33 CDT
Interesting ports on 221.192.199.48:
Not shown: 981 closed ports
PORT     STATE    SERVICE        VERSION
21/tcp   open     tcpwrapped
25/tcp   open     smtp           Microsoft ESMTP 6.0.3790.4675
53/tcp   open     domain         ISC BIND 9.4.2-P2
119/tcp  open     nntp           Microsoft NNTP Service 6.0.3790.3959 (posting ok)
135/tcp  filtered msrpc
139/tcp  filtered netbios-ssn
161/tcp  filtered snmp
445/tcp  filtered microsoft-ds
563/tcp  open     snews?
593/tcp  filtered http-rpc-epmap
1025/tcp open     msrpc          Microsoft Windows RPC
1026/tcp open     msrpc          Microsoft Windows RPC
1027/tcp open     msrpc          Microsoft Windows RPC
1028/tcp open     msrpc          Microsoft Windows RPC
3389/tcp open     microsoft-rdp  Microsoft Terminal Service
4444/tcp filtered krb524
5800/tcp filtered vnc-http
5900/tcp filtered vnc
9999/tcp open     http           Microsoft IIS webserver 6.0
Device type: general purpose
Running (JUST GUESSING) : OpenBSD 4.X (89%)
Aggressive OS guesses: OpenBSD 4.0 (89%)
No exact OS matches for host (test conditions non-ideal).
Network Distance: 17 hops
Service Info: Host: ddisp-56553421; OS: Windows

OS and Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 79.48 seconds

```
I doubt a hacker (cracker, script kiddy, whatever) would run a Windows server with an SMTP and terminal services server. That server was probably compromised, and is now being used to attack other servers.

---

### Post by nightwolf2k5 on 2010-04-22
thank ya'll so much for the advice.. will take out the remote desktop option and will probably stick to team viewer..

i wonder what would've happened if it had been a windows machine..

---

### Post by bodhi.zazen on 2010-04-22
> **cdenley said:**
> That server was probably compromised, and is now being used to attack other servers.

Nice post.

Either that or the ipaddress was spoofed =)

---

### Post by a.walker on 2010-04-22
> **nightwolf2k5 said:**
> Hi there,

I recently put my ubuntu laptop on DMZ on my router.. 

Is there any particular reason why you are putting your laptop in a DMZ? Routers usually have built-in firewalls that help protect the computers that are behind them. When you put it in a DMZ, you're getting rid of that extra protection. 

My router logs show about 50 or so port scans per day. They're fairly common. You probably didn't notice them before because your router's firewall was filtering them out.

---

### Post by HermanAB on 2010-04-23
Hmm, consider yourself very lucky. VNC is horribly insecure and there are automated attack scripts on the web.  You got targeted, but fortunately it did not work.

Install SSH and SSH-Server.  Remove VNC post haste.

---

### Post by rookcifer on 2010-04-23
That IP address shows up in my router logs constantly.  It usually scans ports 2479 or 3246.  There are other machines within the same subnet (221.192.199.*) that also scan me constantly, often on port 8085.  Most likely it is a machine from China running a pirated version of Windows that hasn't been updated and is now part of a botnet.  Or it could be kids at a university scanning for open proxies (since several IP's from that range are always scanning).  Or it could be an enterprise that has had multiple machines compromised.

But there is nothing to worry about.  They aren't targeting you specifically.

---

