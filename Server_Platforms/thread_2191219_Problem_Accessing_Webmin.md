---
title: "Problem Accessing Webmin"
date: 2013-12-01
forum: Server Platforms
---

### Post by greak94 on 2013-12-01
Hi, after struggling for hours I finally was able to come up with a code that installed webmin successfully with my server. It gave me a [https://myhost:port](https://myhost:port) link and I inserted it into multiple browsers and it would not load. I decided to try running /etc/webmin/start and the following error came up. [B]Failed to bind to port 10010 : Address already in use could not listen to on any portsroot
[/B]
After checking there was a port being used by a perl script, so I changed the webmin port and listen to 10010. However, it's still not working. The only thing I could think of might be the issue I don't really know how to code to check. If any solutions with codes could be provided that would help.

---

### Post by rackit on 2013-12-02
Try port 10000 Here is the link I used to install [http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-12-04-precise-server.html) and it works fine.

---

### Post by DommerD on 2013-12-02
I've installed it a few times on my Ubuntu servers, never had an issue.  I use the Webmin apt repository.  See here:
[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

Also, you may have a service running already on port 10000.  See what's running:
netstat --listen

If you need to, look at /etc/services to see what services are registered on what ports.  See if anything is registered for 10000.

---

