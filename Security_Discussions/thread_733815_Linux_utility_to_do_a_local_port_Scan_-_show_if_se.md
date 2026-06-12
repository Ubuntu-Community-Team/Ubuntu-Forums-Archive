---
title: "Linux utility to do a local port Scan - show if server is listening on certain port?"
date: 2008-03-24
forum: Security Discussions
---

### Post by kevdog on 2008-03-24
Is there a built-in Linux utility that allows me to do a local port scan (I'm sitting behind a router and would like to know what ports I have open -- rather than looking at the iptables)?

Also is there a command on the server I can type that would show me if a process is listening on a specific port?  I  always thought nestat -an would do this, but the manual would suggest otherwise.

---

### Post by bhavi on 2008-03-24
Netstat can do the trick as far as I have seen.. But nmap is a indepth port scanner..

```
nmap -sS locahost
```

returns which ports are open on the machine..

Anyway, as I said netstat is much better for use on the local computer than nmap is. Run

```
netstat -antuwp | egrep "(^[^t])|(^tcp.*LISTEN)"
```

to know open ports and what programs that are holding them open.

---

### Post by sillyxone on 2008-03-24
if you need to test incoming connection, there are several free services that perform port scan from their server.

for example: [http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp)

---

### Post by bhavi on 2008-03-24
> **sillyxone said:**
> if you need to test incoming connection, there are several free services that perform port scan from their server.

for example: [http://probe.hackerwatch.org/probe/probe.asp](http://probe.hackerwatch.org/probe/probe.asp)
yes +1 from me...

---

