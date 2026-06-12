---
title: "Setting up web server"
date: 2011-08-01
forum: Server Platforms
---

### Post by scottykal12 on 2011-08-01
So, I have a problem getting my web server to get on the net. If I try to access it on any of the computer on my net work it works but if i try to connect through any other network it doesn't work.

I have forwarded port 80. Any suggestions will be appreciated.

I used this tutorial to get me set up.
[part 1] [http://www.makeuseof.com/tag/build-linux-web-server-computer-part-1/](http://www.makeuseof.com/tag/build-linux-web-server-computer-part-1/)
[part 2] [http://www.makeuseof.com/tag/build-linux-web-server-computer-part-2/](http://www.makeuseof.com/tag/build-linux-web-server-computer-part-2/)

---

### Post by lisati on 2011-08-01
*Thread moved to **Server Platforms**.*

Sometimes ISPs block port 80. When I was setting up my server, I had to ask mine to unblock port 80, and for that to work, I had to organise a static IP address with them.

---

### Post by Lars Noodén on 2011-08-01
> **lisati said:**
> 
Sometimes ISPs block port 80.

You can check if the port is blocked or not with various tools.  One is here:
[http://canyouseeme.org/](http://canyouseeme.org/)

---

### Post by scottykal12 on 2011-08-01
I also tried to use port 8080 to get around this and it's still a no go so im assuming its not a blocked port 80 that is the problem. Also when I disable port 80 the computers in my house cannot connect to the server.

---

### Post by scottykal12 on 2011-08-01
NM port 80 is blocked and I was able to get 8080 working thank you guys.

---

