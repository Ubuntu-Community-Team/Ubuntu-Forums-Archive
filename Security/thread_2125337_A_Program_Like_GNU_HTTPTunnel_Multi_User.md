---
title: "A Program Like GNU HTTPTunnel Multi User"
date: 2013-03-13
forum: Security
---

### Post by leomoon on 2013-03-13
Hello,

I need to setup a linux HTTP Tunnel server that supports multiuser to bypass a very restrictive firewall that only allows HTTP requests. I already tried GNU HTTPTunnel with Squid Proxy (Squid on port 8080) which is exactly what I need but it only supports one user at a time. Do you know any other way to achieve the same thing and possibly easy to connect for windows users?

I already tried HTTPTunnel at: [http://sourceforge.net/projects/http-tunnel/](http://sourceforge.net/projects/http-tunnel/)
But I couldn't set it up properly and I can't find any good tutorial on it either!

Just to show what has been done with GNU HTTPTunnel, here are the instructions below.

**GNU HTTPTunnel Server (hts) on server side:**
#install Squid and configure it on port 8080
apt-get install httptunnel
hts -F localhost:22 80

**GNU HTTPTunnel Client (htc) on Windows side:**
htc -F 10022 linuxServerIP:80
putty -ssh -l prxusr -pw passpassi localhost -P 10022 -L 10023:localhost:8080
#firefox HTTP proxy setting: localhost:10023

Tnx.

---

### Post by cariboo on 2013-03-14
We do not support this type of activity here. If you want help bypassing restrictions put in place, by countries. companies, educational institutes or parents, you'll have to go elsewhere for help. Thread closed.

---

