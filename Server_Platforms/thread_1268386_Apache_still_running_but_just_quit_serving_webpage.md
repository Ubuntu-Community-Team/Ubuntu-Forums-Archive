---
title: "Apache still running but just quit serving webpages..."
date: 2009-09-16
forum: Server Platforms
---

### Post by duneratt on 2009-09-16
I've been running this installation of Apache on Ubuntu (Hardy Heron) for some months now and it just quit serving up the website. Nothing appears to have changed and I don't see any apparent errors with Apache. It is still running but the web page just quit serving up. Not an Ubuntu or Apache guru, how do I debug?

---

### Post by Wim Sturkenboom on 2009-09-17
First question is what kind of errors the browser gives?

Is this a local network or a is the server connected to the internet? How?

You can check apache's access_log and error_log (e.g. *tail -f /var/log/apache/access_log*). You can check the network settings (*ifconfig)*.

Does restarting apache solve it? Do you still have disk space (*df -h*)?


Note:
terminal commands in italic

---

### Post by duneratt on 2009-09-18
The server box is on a home network behind a router that is connected to the internet and isp. I can't even hit the website locally though. They did change the antenna for my wireless net and had to change my static IP but I repointed the domain name and it has worked for about 2 weeks now. It just quit working one afternoon. I checked it from outside of the router about 3 oclock then that night I tried to hit it from within and it wasn't there. I can't find any changes in the config files but then there are a lot and I'm not that schooled on linux or ubuntu. I'm thinking of doing a complete re-install with jaunty. I ran those commands you recommended but couldn't see anything wrong.  my disk space is at 5%.

---

