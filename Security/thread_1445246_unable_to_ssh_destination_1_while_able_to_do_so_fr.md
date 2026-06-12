---
title: "unable to ssh destination_1 while able to do so from different machine."
date: 2010-04-02
forum: Security
---

### Post by adhg on 2010-04-02
Hi all,

I have recently upgraded my ubuntu to 9.10. I'm trying to do this from the command line:

ssh [email]adhg@destination_ONE.com[/email] --> unable to access.

when I do this:
ssh [email]adhg@destination_TWO.com[/email] it works fine

when I do [email]adhg@destination_ONE.com[/email] from a different computer *on the same network* - it works fine. RRrrrr. 

Does anyone have any idea why this happens and how can I fix this?
Thank you.

---

### Post by cdenley on 2010-04-02
Posting the actual output of your connection attempts might be useful. Run these commands on both computers, and post the output here.
```

ssh -v adhg@destination_ONE.com
nc -z -v destination_ONE.com 22
dig destination_ONE.com

```

---

### Post by adhg on 2010-04-02
from my machine (that can't access):

#ssh -v [email]adhg@destination_ONE.com[/email]

OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to destination_ONE.com [xxx.xx.60.150] port 22.
----------------------------------------------------------------------
#nc -z -v destination_ONE.com 22

DNS fwd/rev mismatch: todestination_ONE.com != static-xxx-xx-60-150.ny325.east.verizon.net
----------------------------------------------------------------------
#dig destination_ONE.com
; <<>> DiG 9.6.1-P2 <<>> destination_ONE.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 61640
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;destination_ONE.com.			IN	A

;; ANSWER SECTION:
destination_ONE.com.		404	IN	A	xxx.xx.60.150

;; Query time: 0 msec
;; SERVER: xx.40.1.11#53(xx.40.1.11)
;; WHEN: Fri Apr  2 14:45:57 2010
;; MSG SIZE  rcvd: 48

=============================================================

from the computer that able to access (on the same network)

# nc -z -v destination_ONE.com 22
DNS fwd/rev mismatch: destination_ONE.com != static-xxx-xx-60-150.ny325.east.verizon.net
destination_ONE.com [xxx.xx.60.150] 22 (ssh) open

--------------------------------------------------------------
#dig destination_ONE.com

; <<>> DiG 9.4.2-P2 <<>> [email]adhg@destination_ONE.com[/email]
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 38044
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;adhg\@destination_ONE.com.		IN	A

;; ANSWER SECTION:
adhg\@destination_ONE.com.	0	IN	A	zz.ccc.65.132

;; Query time: 354 msec
;; SERVER: xx.40.1.11#53(10.40.1.11)
;; WHEN: Fri Apr  2 15:54:48 2010
;; MSG SIZE  rcvd: 55



Thanks for any help

---

### Post by cdenley on 2010-04-02
You really messed up those commands.

1. Post any commands or output with "CODE" tags. It makes it much easier to read.
[NOPARSE]
```

output goes here

```
[/NOPARSE]

2. The first few commands don't appear to have finished. The first should have timed out eventually.
```

cdenley@ubuntu:~$ ssh -v 192.168.0.12
OpenSSH_5.1p1 Debian-6ubuntu2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Connecting to 192.168.0.12 [192.168.0.12] port 22.
[B]debug1: connect to address 192.168.0.12 port 22: No route to host
ssh: connect to host 192.168.0.12 port 22: No route to host[/B]

```

3. I could tell by the output you posted, the second command you actually ran was "dig [email]adhg@destination_ONE.com[/email]".

Still, from what I could decipher, it doesn't appear to be a name resolution issue. You're probably using fail2ban or denyhosts on the server, and got yourself banned.
```

sudo iptables -L -n
cat /etc/hosts.deny

```

---

