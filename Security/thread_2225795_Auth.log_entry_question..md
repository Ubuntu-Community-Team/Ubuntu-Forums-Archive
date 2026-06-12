---
title: "Auth.log entry question."
date: 2014-05-23
forum: Security
---

### Post by vRanger on 2014-05-23
Here are a few entries in my Auth.log from today
```
May 23 00:39:25 mailhost sshd[15491]: Failed password for invalid user test from 85.72.245.159 port 49493 ssh2
May 23 02:02:40 mailhost sshd[15832]: Failed password for root from 116.10.191.206 port 26427 ssh2
May 23 04:48:27 mailhost sshd[16658]: reverse mapping checking getaddrinfo for 160.192.163.222.adsl-pool.jlccptt.net.cn [222.163.192.160] failed - POSSIBLE BREAK-IN ATTEMPT!
May 23 04:48:27 mailhost sshd[16650]: Failed password for root from 222.163.192.160 port 39796 ssh2

```
I'm wondering why sometimes it reports "POSSIBLE BREAK-IN ATTEMPT!" like in line 3, and other times, like in line 1,2, & 4, it doesn't.  Seems like they are all break-in attempts, which I understand is not unusual, hence implementation of fail2ban.  I'm just wondering what the difference is.

---

### Post by SeijiSensei on 2014-05-23
It's a different type of problem.  The forward and reverse DNS lookups for that host do not match:
```

$ host 222.163.192.160
160.192.163.222.in-addr.arpa domain name pointer 160.192.163.222.adsl-pool.jlccptt.net.cn.
$ host 160.192.163.222.adsl-pool.jlccptt.net.cn
Host 160.192.163.222.adsl-pool.jlccptt.net.cn not found: 3(NXDOMAIN)

```

---

### Post by untrustytahr on 2014-05-23
The difference is the event which triggered the message.  An incorrect password isn't unusual... especially if you're a fat finger typist, but a failed reverse lookup would be unusual in a correctly configured system.    edit: SeijiSensei is quicker than I :)

---

### Post by vRanger on 2014-05-24
None the less, thank you both for your response!

---

### Post by lisati on 2014-05-24
Good idea looking into tools such as fail2ban.

On a side note, 222.163.192.160 seems to have caught the attention of those who run cbl.abuseat.org - [http://cbl.abuseat.org/lookup.cgi?ip=222.163.192.160](http://cbl.abuseat.org/lookup.cgi?ip=222.163.192.160)

---

### Post by papibe on 2014-05-24
Oh boy :(
```
116.10.191.*
```
Well know source of slow brute force attacks. They'll try every port, and the most common users (root, admin, etc).

I'd recommend adding a rule of this sorts to your iptables:
```
iptables -A INPUT -s 116.10.191.0/24 -j DROP
```
Just a thought.
Regards.

---

### Post by vRanger on 2014-05-24
Good ideas, thanks.  This guy shows how to config fail2ban to permanently ban repeat offenders.  Not exactly beginner level, but VERY cool.
> [http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/](http://stuffphilwrites.com/2013/03/permanently-ban-repeat-offenders-fail2ban/)

---

### Post by unspawn on 2014-05-24
> **vRanger said:**
> This guy shows how to config fail2ban to permanently ban repeat offenders. He could easily have dumped all those addresses in *one single ipset* and be done with it. No need to "pollute" the filter table or the fail2ban chain with that.

---

