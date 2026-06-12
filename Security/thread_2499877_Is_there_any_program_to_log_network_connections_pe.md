---
title: "Is there any program to log network connections per program?"
date: 2024-08-13
forum: Security
---

### Post by u4634456 on 2024-08-13
Hi!

With [FONT=lucida console]*netstat -tnp*[/FONT] I can see currently active internet connections together with with processes.

For example here I can see that connection to 34.107.243.93 was made by firefox:
```
tcp        0      0 192.168.1.125:55822     34.107.243.93:443       ESTABLISHED 2699/firefox-esr 
```

Is there any tool that can get process like netstat but that can log all connections instead of displaying them and that doesn't depend on timing? By timing I mean that netstat for example even in continuous mode just keeps reading */proc/net/tcp** every second which means that if program finishes communication with less than second, it has chance of not showing up in that list.

It seems kinda strange that for Windows even free tools such as Process Monitor can show connections  per process in live and now in Linux there seem none - I mean plenty of programs that can log connections like Sniffet or Ntopng or iptables but none of them can associate connection with process. And it's hard to believe that *netstat* is the only tool that can associate connections with programs that made them. So I decided to come here to see what others know.

---

### Post by TheFu on 2024-08-14
tcpdump  You'll need to got through the logs and probably merge information from multiple logging sources. May need to turn up logging to get everything required.

Linux isn't MS-Windows.  Deep down, they are very, very, different OSes.  All the families of Unix-like OSes have much more in common to each other than any of them have in common with MSFT OSes.

There's an application firewall that GUI users seem to like called **opensnitch**. [https://github.com/evilsocket/opensnitch](https://github.com/evilsocket/opensnitch)  I found it troublesome, but lots of people like the way it can be used to log and block network connections for specific applications and users.

Anyway, best not to assume that just because YOU haven't found a tool, that it doesn't exist or can't trivially be created with a little scripting.  It is a different philosophy than MSFT.  Users are expected to build their own tools by putting a few little programs together to achieve the goal.

---

### Post by Rubi1200 on 2024-08-15
Would this work better for your needs?
```
sudo ss -tulnp

```

There is also a program called Glances but I have never used it so cannot comment on whether it would suit your needs.
[https://nicolargo.github.io/glances/](https://nicolargo.github.io/glances/)

---

### Post by currentshaft on 2024-08-15
.

---

