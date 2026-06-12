---
title: "Setting up a Ubuntu Server"
date: 2009-07-01
forum: Server Platforms
---

### Post by computerman88 on 2009-07-01
I have a HP desktop with a 2.4 GHZ processor and 1GB of RAM and I want to turn it into a server.

[LIST]
[*]VPN server
[*]Windows File Server
[*]VM server (ran by VMware Server)
[/LIST]

If anybody has some links to some web how-to's. I would like to use webmin and ssh to maintain the server.

---

### Post by ericab on 2009-07-01
to be honest, if your going to use webmin (which you should) you dont need any how-to's. webmin makes server administration dead simple.

---

### Post by blueridgedog on 2009-07-01
Here is a bookmark I have used:

[http://www.howtoforge.org/perfect-server-ubuntu8.04-lts](http://www.howtoforge.org/perfect-server-ubuntu8.04-lts)

---

### Post by blsmit on 2009-07-01
Sorry to burst in on this thread but I have a question.

blueridgedog: will this work on a system that is connected cable modem-> router -> server?  Even if the ISP "doesn't allow servers".

Thanks, 
Ben

---

### Post by t4thfavor on 2009-07-01
Yeah, but you will have to setup nonstandard ports (i.e 8080 for web, and 2100 for FTP) as the ISP will block the standard ports.

---

### Post by blsmit on 2009-07-02
T4thfavor,

Would the How to you linked to work for me if I changed the ports to 8080 and 2100?

Thanks, 

Ben

---

### Post by blueridgedog on 2009-07-03
> **blsmit said:**
> Sorry to burst in on this thread but I have a question.

blueridgedog: will this work on a system that is connected cable modem-> router -> server?  Even if the ISP "doesn't allow servers".

Thanks, 
Ben

Yes, but you may need to experiment to see what ports your ISP allows you to access.  It is a shame that in today's world the sold to people as something to consume and if you want to provide information you need to pay more.

---

### Post by blsmit on 2009-07-03
Just one last question.  

Does it matter what port I use since I'm not going to be using the standard port?

Thanks once again for your help.

Ben

---

### Post by modprobe on 2009-07-03
You can use any non-standard port you'd like, just don't forget to use the IP + port entry when accessing your VPN or any other web services.
 
Example:
 
if you're running a web server on port 8080, people will use the following to get to your site:
 
[http://yoursite.homeip.net:8080](http://yoursite.homeip.net:8080)
 
:guitar:

---

### Post by blsmit on 2009-07-03
Very cool, thanks

Ben

---

