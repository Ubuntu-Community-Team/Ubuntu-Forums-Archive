---
title: "which ports do I have to open in ufw for msmtp?"
date: 2011-11-05
forum: Security
---

### Post by bvz on 2011-11-05
Hello, I have msmtp installed on my Ubuntu 11.10 server.

I have been setting up ufw and somehow I cannot use msmtp when ufw is active.

Here are my rules as reported by ufw:

```
Status: active

To                         Action      From
--                         ------      ----
15763/tcp                  ALLOW       Anywhere
548/tcp                    ALLOW       172.16.1.0/24
427/tcp                    ALLOW       172.16.1.0/24
4700/tcp                   ALLOW       172.16.1.0/24
4700/tcp                   ALLOW       127.0.0.1
5353/udp                   ALLOW       172.16.1.0/24
56794/udp                  ALLOW       172.16.1.0/24
42826/udp                  ALLOW       172.16.1.0/24
68                         ALLOW       172.16.1.0/24
25                         ALLOW       Anywhere
2525                       ALLOW       Anywhere
465                        ALLOW       Anywhere
15763/tcp                  ALLOW       Anywhere (v6)
25                         ALLOW       Anywhere (v6)
2525                       ALLOW       Anywhere (v6)
465                        ALLOW       Anywhere (v6)

548/tcp                    ALLOW OUT   172.16.1.0/24
427/tcp                    ALLOW OUT   172.16.1.0/24
4700/tcp                   ALLOW OUT   172.16.1.0/24
4700/tcp                   ALLOW OUT   127.0.0.1
5353/udp                   ALLOW OUT   172.16.1.0/24
56794/udp                  ALLOW OUT   172.16.1.0/24
42826/udp                  ALLOW OUT   172.16.1.0/24
68                         ALLOW OUT   172.16.1.0/24
25                         ALLOW OUT   Anywhere
2525                       ALLOW OUT   Anywhere
465                        ALLOW OUT   Anywhere
25                         ALLOW OUT   Anywhere (v6)
2525                       ALLOW OUT   Anywhere (v6)
465                        ALLOW OUT   Anywhere (v6)
```


I have opened ports 25, 2525, and 465 but still no luck.  (My email provider is everyone.net and I normally use port 2525 to email out).  When ufw is disabled, the email is sent by msmtp.  When I enable it again, no dice.

I am new to most of this and could really use a gentle nudge in the right direction.  Thanks!

---

### Post by bvz on 2011-11-05
Update: I figured it out.  Amazing what a little sleep can do for you.

I needed to open port 53 for dns.  This way, it can resolve smtp.everyone.net to an actual ip address.

---

