---
title: "Not able to connect to server over HTTP"
date: 2009-03-07
forum: Server Platforms
---

### Post by magikid on 2009-03-07
Something crazy is going on with my server.  I can't connect to it with HTTP or HTTPS.  Oddly enough though I can fire up links and surf the web though.  I can SSH into it perfectly.  I really have no idea where to start looking or how to fix this.

---

### Post by Iowan on 2009-03-07
Apache is running?

---

### Post by volkswagner on 2009-03-07
It sounds like the ip address for your server may have changed.  Is it set to static?  Can you ping the machine?

You are not gonna believe this.  I had the same exact problem this morning.  I was trying to ssh to my server and got unavail. host error.

My issue was my laptop connected to a neighbors wireless router, not mine.  Are you trying from a wireless machine?

---

### Post by magikid on 2009-03-07
Apache is running. And it's not the ip address itself because I can still SSH into the machine.  I can ping it from another computer on the network and get a response.  My ip address is set to a static 192.168.0.42

---

### Post by mrsteveman1 on 2009-03-07
You are doing all this on one network, its a server inside your house on your local LAN right?

SSH into the server and run:

> sudo netstat -l | grep http

You should get something out of that command saying it is listening on that port.

Also see if there are firewall rules setup for some reason:

> sudo iptables -L

If you have turned on UFW or something there may be rules in there blocking something.

Are you getting a browser "can't connect to server" page or a 404 or a blank white space or what?

---

### Post by magikid on 2009-03-08
I was just sitting here writing out a response and decided on a lark to check UFW even though I knew that it was disabled and sudo ufw status returned firewall not loaded.  I ran sudo ufw disable though and now everything works perfectly.  Thanks for all the help everyone.

---

