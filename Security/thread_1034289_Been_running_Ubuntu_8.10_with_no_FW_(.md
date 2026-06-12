---
title: "Been running Ubuntu 8.10 with no FW :("
date: 2009-01-08
forum: Security
---

### Post by spennyb on 2009-01-08
Hello all,

Thanks in advance for any replies. I reinstalled Ubuntu 8.10 about 2 mnts ago and forgot to re-enable iptables using ufw.

Yesterday i was downloading a copy of Opensolaris and had iplist open and running (Installed 2 days ago) and noticed packets from a few Uni's blocked and am now wondering that before I had these 2 installed could I have been compromised.

I have no open servcices (Have not enabled anything, i.e as installed as out of the box) and cannot ftp/ssh/telnet/rsh etc to the system but I do see...

# netstat -tlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address
State       PID/Program name
tcp        0      0 localhost:ipp           *:*
LISTEN      5140/cupsd      
tcp        0      0 localhost:smtp          *:*
LISTEN      5652/exim4      

Need I worry ?.

I have run rkhunter and It did complain about the following which from searching does not look to be an issue...

[07:10:55] /usr/sbin/unhide                                  [ Warning ]
[07:10:55] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[07:10:56] /usr/sbin/unhide-linux26                          [ Warning ]
[07:10:56] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.


[07:12:27]   Checking /dev for suspicious file types         [ Warning ]
[07:12:27] Warning: Suspicious file types found in /dev:
[07:12:27]          /dev/shm/pulse-shm-3093154756: data

Need I worry ? or is there any other checks I can do ?.

Thx again in advance
Spence.

---

### Post by hyper_ch on 2009-01-08
iptables is activated by default.

An no, nothing to worry about.

---

### Post by spennyb on 2009-01-08
Thanks for the reply hyper_ch, I got worried when 'ufw status' showed it as disabled and I did have to enable it last time if that makes sense. Sorry if im missing the point.

Spence.

---

### Post by hyper_ch on 2009-01-08
by default is has no rules in it hence it lets everything pass which is good.

---

### Post by cdenley on 2009-01-08
If your only services were listening on "localhost", then a firewall would have accomplished nothing, and you have nothing to worry about.

---

### Post by spennyb on 2009-01-08
Thanks for both of your replies.

Spence.

---

