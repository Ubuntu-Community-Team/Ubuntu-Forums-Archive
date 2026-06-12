---
title: "MTA - At a loss"
date: 2012-05-11
forum: Server Platforms
---

### Post by RefinersFire on 2012-05-11
I need an MTA on my server, but nothing I do is working. I followed the instructions in [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix). I also tried using Webmin. 

Current setup is Postfix & Dovecot. When I try connecting with any email client, I get either connection refused, or unable to get greeting. I tried both IMAP & POP.

I need a good set of instructions, including how to keep the ports open. I am not using a firewall yet. Apache and BIND both work fine.

Thanks

---

### Post by mathcolo on 2012-05-12
I'm not sure if this will help you or not, but it seems to be a helpful set of instructions for setting up some basic things (including Dovecot) on Ubuntu 12.04 server:

[http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3](http://www.howtoforge.com/perfect-server-ubuntu-12.04-lts-nginx-bind-dovecot-ispconfig-3)

Good luck!

---

### Post by SeijiSensei on 2012-05-12
Are you trying to connect over the network, or are you connecting via the localhost interface on the machine itself?

By default both Postfix and sendmail are bound to the localhost (127.0.0.1) interface for security reasons.  On the machine running Postfix, what happens if you run "telnet localhost 25"?  Do you get the Postfix banner?  Now try "telnet ip.of.the.machine 25" using the machine's eth0 address.  Does it connect?  If not you need to fix  the inet_interfaces and my_networks directives in Postfix's main.cf [configuration file]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#inet_interfaces").

---

### Post by RefinersFire on 2012-05-13
mathcolo: Thanks, I will check it out.

SeijiSensei: I have set both Postfix and Dovecot to both local host, and my domain. When I port scan 127.0.0.1 , I get: ```
Port	State	Service
25	open	smtp
53	open	domain
80	open	www
631	open	ipp
953	open	unknown
3306	open	mysql
10000	open	webmin
10100	open	unknown

```

When I scan my IP address or domain, I get: ```
Port	State	Service
25	open	smtp
53	open	domain
80	open	www
10000	open	webmin
10100	open	unknown
45845	open	unknown

```

Okay, that's not exactly what I was getting. 110 & 143 were included in earlier scans of 127.0.0.1, but never in my domain or IP address scans.

First issue. I can't keep 143, 110, and 25 open all at once. Either 110 and 143 are closed, or their both open and 25 is closed. 

When I do connect to port 25 (POP or IMAP) I get the errors above. When I do connect to 110 or 143, I get an error scanning folders with any mail client (second issue).

I have even completely removed Postfix & Dovecot and re-installed.


:confused:

---

### Post by abix_adam_pl on 2012-05-13
Could you post your main.cf file?

---

