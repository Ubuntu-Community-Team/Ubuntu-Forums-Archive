---
title: "stuck in openfire setup/installation"
date: 2009-03-26
forum: Server Platforms
---

### Post by artheus on 2009-03-26
Hey..

I've installed the Openfire package using the tar.gz onthis site
[http://www.igniterealtime.org/downloads/index.jsp]("http://www.igniterealtime.org/downloads/index.jsp")
on my Ubuntu Server Edition 8.10. I do not have the GUI installed. so I am running "terminal-only" (or whatever is the correct way of saying that.)

Soo.. I have followed this guide
[http://www.igniterealtime.org/builds/openfire/docs/latest/documentation/install-guide.html#config]("http://www.igniterealtime.org/builds/openfire/docs/latest/documentation/install-guide.html#config")
And configured my mysql, which worked great. But now I want to connect to the "Openfire setup tool" as it is refered to. And for that I need a browser.
I have this desktop pc with firefox. But can't seem to get to the openfire setup page.
It's said that I should go to [http://127.0.0.1:9090](http://127.0.0.1:9090) if I am on the same machine as the openfire. But I am not. So I figured [http://192.168.1.39:9090](http://192.168.1.39:9090) should work, because that is the correct adress for my server. But it failed. I get an "404" error.

What am I doing wrong?

And when I am trying to make the command "sudo /etc/init.d/openfire start/restart/stop" I get "bash: /etc/init.d/openfire: Permission denied"

What? As the root user I get permission denied!?

well.. thanks in advance!

Cheers,
Artheus

---

### Post by artheus on 2009-03-26
Well found out now that I have to use
"/opt/openfire/bin/openfire start" to start the service.. But It only replies "sudo: /opt/openfire/bin/openfire: command not found"

hmmm..:confused:

---

### Post by Martym on 2009-04-22
Do you have port 9090 forwarded to 192.168.1.39 on your router/firewall?

---

### Post by artheus on 2009-04-23
Well. Yes I believe so, because on my server I have set the "default server" to 192.168.1.39, which the router manual says should forward all ports to my server.

---

