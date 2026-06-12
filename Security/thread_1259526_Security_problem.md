---
title: "Security problem?"
date: 2009-09-06
forum: Security
---

### Post by satwien on 2009-09-06
I found this sequence in /var/log/proftpd.log

```
Sep 06 00:59:05 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:06 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:06 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:06 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:06 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:07 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:07 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:07 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:07 ubu904 proftpd[30549] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:07 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:08 ubu904 proftpd[30550] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:09 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:09 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:09 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:10 ubu904 proftpd[30551] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:11 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:11 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:11 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:12 ubu904 proftpd[30552] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:12 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:13 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:13 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:13 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:13 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:14 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:14 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:14 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:14 ubu904 proftpd[30553] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:14 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:15 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:15 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:15 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:15 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:16 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:16 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:16 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:16 ubu904 proftpd[30554] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:16 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:17 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:17 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:17 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:17 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:18 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:18 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:18 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:18 ubu904 proftpd[30555] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:18 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:18 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:18 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:19 ubu904 proftpd[30557] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:20 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:21 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:21 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:21 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:21 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:22 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:22 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:22 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:22 ubu904 proftpd[30558] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:22 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:23 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:23 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:23 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:23 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:24 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:24 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:24 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:24 ubu904 proftpd[30559] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 00:59:24 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session opened.
Sep 06 00:59:24 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:24 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): no such user 'Administrator'
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): USER Administrator: no such user found from server.tlthinc.com [::ffff:65.83.80.220] to ::ffff:192.168.10.111:21
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): Maximum login attempts (3) exceeded, connection refused
Sep 06 00:59:25 ubu904 proftpd[30560] ubu904 (server.tlthinc.com[::ffff:65.83.80.220]): FTP session closed.
Sep 06 13:38:21 ubu904 proftpd[31292] ubu904 (::ffff:159.148.243.15[::ffff:159.148.243.15]): FTP session opened.
Sep 06 13:38:21 ubu904 proftpd[31292] ubu904 (::ffff:159.148.243.15[::ffff:159.148.243.15]): SECURITY VIOLATION: root login attempted.
Sep 06 13:38:21 ubu904 proftpd[31292] ubu904 (::ffff:159.148.243.15[::ffff:159.148.243.15]): FTP session closed.
```

This is only a part of a more than 2 MB log file.
I have a portforward of port 21 from router to Ubuntu server.
That's something to take care? What should I do?
Thx a lot in advance for you answers.

---

### Post by fela on 2009-09-06
If port 21 is open to the internet then yeah that's a very bad idea I think.

---

### Post by Bachstelze on 2009-09-06
> **fela said:**
> If port 21 is open to the internet then yeah that's a very bad idea I think.

But closing port 21 = no FTP...

@satwien: Nothing to worry about. Someone is just try to login as a user who does not exist. If you want them to stop polluting your logs, add them to /etc/hosts.deny or something like that.

---

### Post by satwien on 2009-09-06
Thx m8s! :)

---

### Post by Kinstonian on 2009-09-06
> **HymnToLife said:**
> But closing port 21 = no FTP...

@satwien: Nothing to worry about. Someone is just try to login as a user who does not exist. If you want them to stop polluting your logs, add them to /etc/hosts.deny or something like that.

Password guessing attacks are the #1 reason people post on these forums requesting help after getting hacked.  So I don't know if I'd say it was nothing to worry about.  When it's not possible to switch to a more secure protocol, or limit access to only select IPs with a firewall; In addition to choosing strong passwords, I'd also at least look into setting up a clipping level to automatically slow down this type of attack.

---

### Post by Hobgoblin on 2009-09-06
> **HymnToLife said:**
> But closing port 21 = no FTP...


Well you could use a different port.

---

### Post by Bachstelze on 2009-09-06
> **Kinstonian said:**
> Password guessing attacks are the #1 reason people post on these forums requesting help after getting hacked.  So I don't know if I'd say it was nothing to worry about.  When it's not possible to switch to a more secure protocol, or limit access to only select IPs with a firewall; In addition to choosing strong passwords, I'd also at least look into setting up a clipping level to automatically slow down this type of attack.

Nothing to worry about, assuming the server has a sane security model, of course (strong password, chrooted users, root access disabled, etc.).

> **Hobgoblin said:**
> Well you could use a different port.

You could, but that wouldn't make your server any more secure.

---

### Post by XCan on 2009-09-06
> **HymnToLife said:**
> 
You could, but that wouldn't make your server any more secure.

It wouldn't under the assumption that the bots find out which port it gets moved to. But it will most definitely drop the number of attacks by 99.9% if the port is chosen wisely.

---

### Post by Hobgoblin on 2009-09-07
> **HymnToLife said:**
> 

You could, but that wouldn't make your server any more secure.

No, but it would eliminate these attacks and reduce the chances of script kiddies gaining entry by brute force.

---

### Post by Rob_H on 2009-09-07
You might also want to check to see if [Fail2ban]("http://www.fail2ban.org/wiki/index.php/Main_Page") can be applied here. It will automatically block IP addresses that make too many failed connection attempts.

---

### Post by __p1n__ on 2009-09-07
> **HymnToLife said:**
> Nothing to worry about, assuming the server has a sane security model, of course (strong password, chrooted users, root access disabled, etc.).



You could, but that wouldn't make your server any more secure.

This is my first post so I'll apologize in advance for breaching any putative forum protocol.  IMHO I think that the attack logged has more to do with an IIS ftp vulnerability posted 6 days ago than any attempt to brute-force guess valid login credentials.  The username "Administrator" is also suggestive of this.

There is however a 2 week old Proftp metasploit attack which would be my second guess.

As a countermeasure perhaps you can consider keeping port 21 normally closed and only open it up upon receipt of some out of band event (delivered via a separate, more-secure method.)  This doesn't increase your actual platform security but it does reduce your attack surface (time dimension.)

Make sure that you're fully patched too natch;)

---

### Post by bobince on 2009-09-08
Moving the port is definitely useful for cleaning up security logs in general, so you only see the people who are really trying to hack you and not just internet portscanning background noise.

Blocking IP addresses that provoke too many failures is not a bad idea, but there are botnets that distribute their brute-forcing to avoid this, so it's not enough in itself.

In general, I'd avoid using FTP on the public internet for anything other than anonymous FTP. Anything you have to log in for should be going over SFTP.

---

