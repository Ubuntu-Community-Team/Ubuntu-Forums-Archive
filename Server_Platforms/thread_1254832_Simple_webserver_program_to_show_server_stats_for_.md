---
title: "Simple webserver program to show server stats for disk usage, network traffic, etc.?"
date: 2009-08-31
forum: Server Platforms
---

### Post by flatland2d on 2009-08-31
Last week I built a home server and I was wondering if anyone knows of some simple programs that I can run on it to serve a webpage on the local network showing disk usage, network traffic, running processes... that kind of stuff.

I enabled the web interface on Transmission and and really like being able to see all the info.  This got me thinking about hosting a page for the rest of the server, too.

Thanks for any help.

---

### Post by SoftwareExplorer on 2009-08-31
I've used webmin. It might be in the repositories, I'll have to check.

---

### Post by SoftwareExplorer on 2009-08-31
Ok, read the second half of this page to install webmin:[http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html]("http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html")

---

### Post by flatland2d on 2009-08-31
Webmin looks nice, but it does way more than I want it to, so I guess I see it as a bit of a security issue.  I'd rather not allow control from the web.

---

### Post by SoftwareExplorer on 2009-08-31
What I do with it:Use firewall or NAT to restrict access to just local. Then ssh in with something like 'ssh user@server -L 20000:localhost:10000 -p <port you use for ssh>' which makes a secure and encrypted connection. Then you can go to localhost:20000 in a web browser on the computer I ssh'ed from. That way, you can only connect if you ssh in--and if an attacker gets into ssh, your screwed anyways.

---

