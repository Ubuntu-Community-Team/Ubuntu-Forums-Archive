---
title: "fail2ban's sshd-ddos jail not working"
date: 2017-01-16
forum: Security
---

### Post by waltman on 2017-01-16
I've enabled fail2ban's sshd-ddos jail on 16.10, but it doesn't week to be working. I've got multiple lines in auth.log of the form

Jan 16 16:14:36 hermes sshd[11450]: Did not receive identification string from 113.108.21.16 port 39950

As far as I can tell that's the exact form that sshd-ddos.conf is looking for. However, I don't see any entries for sshd-ddos in fail2ban.log. Fail2ban itself is working, because I see plenty of entries for sshd, and addresses are getting banned appropriately per my settings.

Is this a bug in fail2ban or am I doing something wrong?

---

### Post by Habitual on 2017-01-20
Please issue the following test and report the "Results" and "Summary" sections at the end of the output.
```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf
```

Thank you.

Don't forget [noparse]```
output here
```[/noparse] in your reply.

---

### Post by waltman on 2017-01-20
Did you mean sshd.conf, or sshd-ddos.conf? Here's the output from both:

```
$ fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd.conf

Running tests
=============


Use   failregex filter file : sshd, basedir: /etc/fail2ban
Use         maxlines : 10
Use         log file : /var/log/auth.log
Use         encoding : UTF-8




Results
=======


Failregex: 705 total
|-  #) [# of hits] regular expression
|   3) [447] ^(?:\[\])?\s*(?:<[^.]+\.[^.]+>\s+)?(?:\S+\s+)?(?:kernel: \[ *\d+\.\d+\]\s+)?(?:@vserver_\S+\s+)?(?:(?:(?:\[\d+\])?:\s+[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?|[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?(?:\[\d+\])?:?)\s+)?(?:\[ID \d+ \S+\]\s+)?Failed \S+ for .*? from <HOST>(?: port \d*)?(?: ssh\d*)?(: (ruser .*|(\S+ ID \S+ \(serial \d+\) CA )?\S+ (?:[\da-f]{2}:){15}[\da-f]{2}(, client user ".*", client host ".*")?))?\s*$
|  16) [26] ^(?:\[\])?\s*(?:<[^.]+\.[^.]+>\s+)?(?:\S+\s+)?(?:kernel: \[ *\d+\.\d+\]\s+)?(?:@vserver_\S+\s+)?(?:(?:(?:\[\d+\])?:\s+[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?|[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?(?:\[\d+\])?:?)\s+)?(?:\[ID \d+ \S+\]\s+)?(error: )?maximum authentication attempts exceeded for .* from <HOST>(?: port \d*)?(?: ssh\d*)? \[preauth\]$
|  17) [232] ^(?:\[\])?\s*(?:<[^.]+\.[^.]+>\s+)?(?:\S+\s+)?(?:kernel: \[ *\d+\.\d+\]\s+)?(?:@vserver_\S+\s+)?(?:(?:(?:\[\d+\])?:\s+[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?|[\[\(]?sshd(?:\(\S+\))?[\]\)]?:?(?:\[\d+\])?:?)\s+)?(?:\[ID \d+ \S+\]\s+)?pam_unix\(sshd:auth\):\s+authentication failure;\s*logname=\S*\s*uid=\d*\s*euid=\d*\s*tty=\S*\s*ruser=\S*\s*rhost=<HOST>\s.*$
`-


Ignoreregex: 0 total


Date template hits:
|- [# of hits] date format
|  [2506] (?:DAY )?MON Day 24hour:Minute:Second(?:\.Microseconds)?(?: Year)?
`-


Lines: 2506 lines, 0 ignored, 705 matched, 1801 missed
[processed in 1.63 sec]


Missed line(s): too many to print.  Use --print-all-missed to print all 1801 lines

$ fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd-ddos.conf


Running tests
=============


Use   failregex filter file : sshd-ddos, basedir: /etc/fail2ban
Use         log file : /var/log/auth.log
Use         encoding : UTF-8




Results
=======


Failregex: 0 total


Ignoreregex: 0 total


Date template hits:
|- [# of hits] date format
|  [2506] (?:DAY )?MON Day 24hour:Minute:Second(?:\.Microseconds)?(?: Year)?
`-


Lines: 2506 lines, 0 ignored, 0 matched, 2506 missed
[processed in 0.18 sec]


Missed line(s): too many to print.  Use --print-all-missed to print all 2506 lines



$ grep 'Did not receive identification string from' /var/log/auth.log|wc -l
29
```

---

### Post by Habitual on 2017-01-21
Yes, I meant to write ```
fail2ban-regex /var/log/auth.log /etc/fail2ban/filter.d/sshd-ddos.conf
```
but guess what? It's not working, per the test.

I suggest enabling ssh and not ssh-ddos in /etc/fail2ban/jail.local
as it finds 705 abuses.

---

### Post by waltman on 2017-01-21
They don't seem to be mutually exclusive, so I've got both enabled. The ssh one is indeed catching some abuses.

---

### Post by Habitual on 2017-01-22
I am not sure what coverage it provides, but if it's working, that's a Great Start!

---

