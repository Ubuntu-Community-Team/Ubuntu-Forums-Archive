---
title: "Need help"
date: 2009-11-20
forum: Security
---

### Post by kadeous on 2009-11-20
For two days I had this in my log, finally I installed fail2ban and I'm hoping that will workout. I'm learning iptables but in the meantime I'm wondering if I should pull my server offline.
 
Nov 20 06:53:10 syt pop3d: Connection, ip=[::ffff:200.91.9.37]
Nov 20 06:53:10 syt pop3d: LOGIN FAILED, user=solange, ip=[::ffff:200.91.9.37]
Nov 20 06:53:16 syt pop3d: Disconnected, ip=[::ffff:200.91.9.37]
Nov 20 06:53:16 syt pop3d: Connection, ip=[::ffff:200.91.9.37]
Nov 20 06:53:16 syt pop3d: LOGIN FAILED, user=soloman, ip=[::ffff:200.91.9.37]
Nov 20 06:53:21 syt pop3d: Disconnected, ip=[::ffff:200.91.9.37]
Nov 20 06:53:22 syt pop3d: Connection, ip=[::ffff:200.91.9.37]
Nov 20 06:53:22 syt pop3d: LOGIN FAILED, user=soman, ip=[::ffff:200.91.9.37]
Nov 20 06:53:27 syt pop3d: Disconnected, ip=[::ffff:200.91.9.37]
Nov 20 06:53:27 syt pop3d: Connection, ip=[::ffff:200.91.9.37]
Nov 20 06:53:28 syt pop3d: LOGIN FAILED, user=somasama, ip=[::ffff:200.91.9.37]
 
I'm guessing the person is trying to gain access to my Pop3 server to send out spam e-mails?

---

### Post by Yoann Juet on 2009-11-21
> **kadeous said:**
> For two days I had this in my log, finally I installed fail2ban and I'm hoping that will workout. 
...
Nov 20 06:53:21 syt pop3d: Disconnected, ip=[::ffff:200.91.9.37]


::ffff:200.91.9.37 is an IPv6 address not an IPv4 one. I don't think that Fail2ban yet supports IPv6 protocol. You'd better disable IPv6 if not absolutely necessary.

---

### Post by fahadsadah on 2009-11-21
::ffff:200.91.9.37 is an IPv4 address in IPv6 notation, often given by apps that only support v6.

Disabling IPv6 will not help.

---

### Post by JBAlaska on 2009-11-21
just block the ip in iptables

```
iptables -A INPUT -s ipaddr -j DROP
```

---

### Post by fahadsadah on 2009-11-21
I've just checked the address. It is hosting [http://www.parallelchile.cl/](http://www.parallelchile.cl/), and also a (closed) HTTP proxy.

For abuse from that address, email [email]manuel.orellana@TELEFONICA.COM[/email] or call +56 02 7701511. You can also write to ```

San Martin 50 Piso 6, 0,
8340526 - Santiago -
Chile

```
The registered contact for the address is Manuel Orellana Carrera, who is presumably an employee of CTC Transmisiones Regionales S.A.

---

### Post by Yoann Juet on 2009-11-21
> **fahadsadah said:**
> ::ffff:200.91.9.37 is an IPv4 address in IPv6 notation, often given by apps that only support v6.

Disabling IPv6 will not help.

:D you're right, this is not a valid IPv6 routing prefix. According to fail2ban manual, such a notation is already supported :

"As a convenience, you can use the predefined entity <HOST> in your regexes. <HOST> is an alias for (?:::f{4,6}:)?(?P<host>\S+), which matches either a hostname or an IPv4 address (possibly embedded in an IPv6 address)"

You should not have difficulties automatically blocking attackers with this tool. It may just need a little tweaking.

---

### Post by kadeous on 2009-11-21
You guys rock! I'm still learning the security portion of Ubuntu and today's log revealed no further attacks.

---

