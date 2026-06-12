---
title: "UFW - can't block port 80"
date: 2010-11-15
forum: Security
---

### Post by _ex_ on 2010-11-15
Hello everyone!


I have problem with ufw and port 80. Here's the status of ufw:
```
Status: active
Logging: on (full)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
23                         DENY IN     Anywhere
9000                       DENY IN     Anywhere
10000                      DENY IN     Anywhere
3306                       DENY IN     Anywhere
21                         DENY IN     Anywhere
80                         DENY IN     Anywhere
631                        DENY IN     Anywhere
```I tried to check ports with nmap:
```
$ sudo nmap -sS ??????????????????
Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-15 13:45 CET
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.28 seconds
```I also tried with -PN:
```
$ sudo nmap -PN ???????????????
Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-15 13:45 CET
Interesting ports on ???????????? (?????????????/):
Not shown: 999 filtered ports
PORT   STATE SERVICE
80/tcp open  http

Nmap done: 1 IP address (1 host up) scanned in 6.83 seconds
```Maybe the problem is that I tried the test from the same IP address? I just followed the instructions I got on other forums..
However, I use lamp, eclipse, git, and a couple of smaller programs that have nothing to do with http and port 80. I just need to be invisible, but able to surf. I do not need any port to be open for incoming traffic. I want to block them all.

This is a very serious problem, because my computer was hacked a few days ago.

Thanks.

---

### Post by Trougedoor122 on 2010-11-15
Port 80 is the port for HTTP, if you block it, you can't browse the web from any web browser.

---

### Post by cariboo on 2010-11-15
Yes if you run nmap on the same system you will get different results than if you run it from another system on your internal network. 

This the result if I run nmap on my server:

```
nmap willy

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-15 10:27 PST
Interesting ports on willy.APLUS (127.0.1.1):
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
3389/tcp open  ms-term-serv

Nmap done: 1 IP address (1 host up) scanned in 0.11 seconds
```

This is the result if I run nmap from another system on my network with the firewall enabled on the server:

```
map willy

Starting Nmap 5.21 ( http://nmap.org ) at 2010-11-15 10:27 PST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.06 seconds
```

BTW I was just using the default rules, and everything was blocked.

---

### Post by bodhi.zazen on 2010-11-15
It is impossible to determine from what you posted.

In general:

1. What service are you running that is listening on port 80 ? Either remove it or configure it so that it listens on localhost only.

2. You need to scan with nmap from a second computer.

3. Are you scanning your computer or your router ?

From your post I understand you are concerned and I highly suggest you do some reading on security, in particular iptables and nmap.

---

### Post by spiky001 on 2010-11-15
Would it help to scan from here [http://nmap-online.com/](http://nmap-online.com/)

---

### Post by bodhi.zazen on 2010-11-15
> **spiky001 said:**
> Would it help to scan from here [http://nmap-online.com/](http://nmap-online.com/)

Not if the OP has a router. If one is using a router online scanners only scan the router.

---

### Post by brian_p on 2010-11-15
> **_ex_ said:**
> Hello everyone!

Hello _ex_.

> I have problem with ufw and port 80. Here's the status of ufw: . . . . . . .

You are denying incoming connnections.

Port 23: Usually telnetd. Are you running telnetd? If not, why block connections to a non-existent daemon?

Port 21: Usually ftp. Are you running an ftp server? If not, why block connections to a non-existent daemon?

Port 10000: Usually webmin. Is that operative on your machine.  If not, why block connections to a non-existent daemon?

Ports 3360 and 9000: Only you know what are listening on these ports. If you don't, why block connections to non-existent daemons?

Port 80: Usually a web server. Have you got one?

Port 631: CUPS. Doesn't listen for external connections by default. Blocking is a waste of time and effort.

> This is a very serious problem, . . . . . .

No it's not.

---

### Post by _ex_ on 2010-11-16
Thanks for replies. Some things are clearer to me now. I'll continue reading about security.
Thank you all. ;)

> **brian_p said:**
> 
No it's not.
lol good one :D

---

### Post by teejaybee on 2010-11-16
If you were hacked, and you haven't made a copy of anything important (data - not binaries, libraries, etc) and reinstalled yet, the attacker could have done something to your system to leave access open for him to get back in.

If your system was compromised, I would suggest:

Unplug from the network.
Make an image of the disk for later perusal. (optional)
Copy personal data and custom config files etc to external media
Format and reinstall with the latest distro version and start again.
Examine everything you copy back to the system to ensure it hasn't been tainted in any way.

---

### Post by _ex_ on 2010-11-16
I've already done that, but tnx.
Now just trying to find a reliable way to improve security.

---

