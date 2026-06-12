---
title: "Postfix and port 25"
date: 2013-11-03
forum: Server Platforms
---

### Post by Code9 on 2013-11-03
Hello all,

I am trying to set up a POSTFIX server on my machine. I can telnet to the service locally and it works fine. However, I cannot do so from any remote location. When I used Nmap to see what ports were listening, I got this.

```

Host is up (0.056s latency).
Not shown: 997 filtered ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https

```

I added the rule to ufw, but it doesn't seem to be working.

```

To                         Action      From
--                         ------      ----
25                         ALLOW       Anywhere
22                         ALLOW       Anywhere
80                         ALLOW       Anywhere
443                        ALLOW       Anywhere
25                         ALLOW       Anywhere (v6)
22                         ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6)
443                        ALLOW       Anywhere (v6)

```

Any help is much appreciated.

---

### Post by houstonbofh on 2013-11-04
Almost all ISPs filter port 25 on home connections.  You may need a business connection for it to work.

---

### Post by anh-tct on 2013-11-04
try to telnet port 25 from another machine on your local network to verify that your postfix is good configured , also pls allow postfix to listen on local  IP  instead of 127.0.0.1 IP
if you can telnet port 25 from another machine then all the configuration is ok

---

