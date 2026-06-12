---
title: "does Xen do what i think it will do?"
date: 2008-07-09
forum: Server Platforms
---

### Post by tobycatlin on 2008-07-09
Hello everybody,

I have the need to run a number of custom web servers. Each webserver runs off a different port and each one has a number of supporting components that use similar ports.
eg
web server #1 on 8000
data source #1 on 8010
...
web server #2 on 9000
data source #2 on 9010

This setup is for a test environment so i have the need for 10 servers now but possible many more, say up to 30. Each server is under a very low load, and doesn't consume much resource. comparable to Apache, certainly now more.

Now using Xen i can setup a number of virtual machines, with each one running it's own server instance right? Which means the webservers can run the same ports and all processes are kept separate.
Can one server (assuming a decent quad core and healthy chunk of ram) run this many VM's. My dev machine can't run more than two vm's (using vmware) without everything grinding to a halt.

Does anyone have any better suggestions for achieving this? with or without Xen

I should probably mention i am running ubuntu servers, incase people are thinking why i am posting here

thanks for your time and input
toby

---

### Post by windependence on 2008-07-09
You could do the same thing with VMware, but yes Xen will do what you want. I am not sure you want to run 10 on one box though. I have been OK with 5 but it really depends on what you are running and how you have it set up. I should mention that ALL my guests running Apache are FreeBSD or Open BSD. Much smaller footprint and use much less resources. I use Ubuntu for the host OS though.

-Tim

---

### Post by tobycatlin on 2008-07-09
Thanks thats the kinda feedback i needed

---

