---
title: "Can't recieve emails"
date: 2010-12-01
forum: Server Platforms
---

### Post by kevin11951 on 2010-12-01
I just migrated to a Zimbra email server, but I can't seem to receive emails.

The DNS records seem clean:

```
; <<>> DiG 9.7.1-P2 <<>> any kviero.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 16581
;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;kviero.com.			IN	ANY

;; ANSWER SECTION:
kviero.com.		1591	IN	MX	0 mail.kviero.com.
kviero.com.		1591	IN	MX	10 mail.kviero.com.
kviero.com.		1591	IN	A	99.114.204.65
kviero.com.		84391	IN	SOA	ns11.domaincontrol.com. dns.jomax.net. 2010113003 28800 7200 604800 86400
kviero.com.		1591	IN	NS	ns11.domaincontrol.com.
kviero.com.		1591	IN	NS	ns12.domaincontrol.com.

;; Query time: 33 msec
;; SERVER: 10.0.0.1#53(10.0.0.1)
;; WHEN: Wed Dec  1 09:47:52 2010
;; MSG SIZE  rcvd: 182

```

and "mail.kviero.com" resolves to the correct IP address...

List of open ports if thats important:

```
Starting Nmap 5.21 ( http://nmap.org ) at 2010-12-01 09:45 CST
Nmap scan report for mail.kviero.com (99.114.204.66)
Host is up (0.0044s latency).
rDNS record for 99.114.204.66: 99-114-204-66.uvs.austtx.sbcglobal.net
Not shown: 994 filtered ports
PORT    STATE SERVICE
22/tcp  open  ssh
25/tcp  open  smtp
80/tcp  open  http
465/tcp open  smtps
993/tcp open  imaps
995/tcp open  pop3s

Nmap done: 1 IP address (1 host up) scanned in 6.05 seconds

```

---

### Post by kevin11951 on 2010-12-01
Update:

Is this weird, or am I doing it wrong?

```

**telnet mail.kviero.com 25**

Trying 99.114.204.66...
Connected to mail.kviero.com.
Escape character is '^]'.
220 mail.kviero.com ESMTP Postfix
ehlo
501 Syntax: EHLO hostname

```

---

### Post by CharlesA on 2010-12-01
You need to tell it the hostname.

See [here]("https://help.ubuntu.com/community/Postfix#Testing").

---

