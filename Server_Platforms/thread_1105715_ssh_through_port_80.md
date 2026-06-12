---
title: "ssh through port 80"
date: 2009-03-25
forum: Server Platforms
---

### Post by gishaust on 2009-03-25
I am behind a firewall at school that only has port 80 open. Is there away to access my server over the internet and ssh in on port 22.

---

### Post by littlegreiger on 2009-03-25
One way to do this is to change the port that your ssh server is running on. To do this you need to edit your sshd config file
```
sudo nano -w /etc/sshd_config
```
and change
```
Port 22
```
to
```
Port 80
```

Another port you might try is 443, which is the SSL port. Most likely it won't be blocked by your school and then you still have the option to run a webserver if needed.
Hope that helps

---

### Post by happyhacker on 2009-03-25
I have just setup dyndns to my server and would like to use ssh. I have an ssh server running. How do I link the ssh server in so that all connections from outside use ssh encryption? Or maybe it's not necessary?

---

### Post by BkkBonanza on 2009-03-25
I'll answer the ssh question if you start a new thread and don't hijack this one...

---

### Post by happyhacker on 2009-03-25
Will do, I thought it was useful to extend the discussion!

---

### Post by BkkBonanza on 2009-03-25
We should let the OP respond and help him with his problem first. The case of running ssh through port 80 is quite different from what you likely need for more typical web server use since in his case he doesn't have control of the school router and so is working on a way around that.

---

### Post by gishaust on 2009-03-25
thanks I will scan the ports and see if 443 is open.

---

### Post by windependence on 2009-03-26
443 is your best bet. Not only is it usually open, but the traffic is encrypted anyway, so they really don't know what is passing through it. (of course your tunnel is also secure).

Before anyone say it, I know it's probably against his school policy but there are far worse things he could be doing than mucking with servers. It's a good learning experience.

-Tim

---

