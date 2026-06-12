---
title: "java.net.BindException: Permission denied binding to ports ABOVE 1024"
date: 2010-10-25
forum: Security
---

### Post by cmsimike on 2010-10-25
So here's a weird issue: I'm trying to start resin through eclipse for some development testing, however ever time I try to start it, I get a bind exception:
[19:58:06.504] Server[] starting
[19:58:06.505] 
[19:58:06.505] Linux 2.6.32-25-generic i386
[19:58:06.505] Java 17.1-b03, 32, mixed mode, UTF-8, en, Sun Microsystems Inc.
[19:58:06.505] resin.home = null
[19:58:06.505] server.root = null
[19:58:06.505] 
[19:58:06.512] http listening to *:8081
[19:58:06.671] java.net.BindException: Permission denied
[19:58:06.671] 	at java.net.PlainSocketImpl.socketBind(Native Method)
[19:58:06.671] 	at java.net.PlainSocketImpl.bind(PlainSocketImpl.java:365)
[19:58:06.671] 	at java.net.ServerSocket.bind(ServerSocket.java:319)
[19:58:06.671] 	at java.net.ServerSocket.<init>(ServerSocket.java:185)

I've tried 80, 8081, and 18081. I don't know what's going on and I've not found anything to help me with this problem for ports above 1024. I can start up Resin no problem outside of Eclipse. Any suggestions?

---

