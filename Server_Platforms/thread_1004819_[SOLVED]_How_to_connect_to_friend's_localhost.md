---
title: "[SOLVED] How to connect to friend's localhost"
date: 2008-12-07
forum: Server Platforms
---

### Post by clay7 on 2008-12-07
Hello,
I have a friend who is running Apache on Windows XP. I can call him up and he can instantly give me his IP address from the ISP (24.xx.xx.xxx) (real numbers not shown) as well as his IP info from 'ipconfig' (192.168.1.2). His .conf file is set to listen on port 80. 

How can I see his home directory from my computer? I opened FireFox and tried these:

[http://24.xx.xx.xxx/](http://24.xx.xx.xxx/)
[http://24.xx.xx.xxx/192.168.1.2/](http://24.xx.xx.xxx/192.168.1.2/)
[http://24.xx.xx.xxx/127.0.0.1/](http://24.xx.xx.xxx/127.0.0.1/)
[http://24.xx.xx.xxx/index.html](http://24.xx.xx.xxx/index.html)
[http://24.xx.xx.xxx/index.html:80](http://24.xx.xx.xxx/index.html:80)

...and none of these worked. How do I do this?

Thanks!

---

### Post by littlegreiger on 2008-12-07
It sounds like he hasn't forwarded port 80 on his router to the computer running the webserver.

Tell him to log on to his router, which should be located at 192.168.1.1 and forward port 80 to his computer (192.168.1.2). Then you should be able to type in his real IP address, the one his ISP gave him and you should get to the page he has created.

If you need help figuring out how to forward the ports I would recommend the site [http://www.portforward.com]("http://www.portforward.com")

---

### Post by hictio on 2008-12-07
> **clay7 said:**
> Hello,
I have a friend who is running Apache on Windows XP. I can call him up and he can instantly give me his IP address from the ISP (24.xx.xx.xxx) (real numbers not shown) as well as his IP info from 'ipconfig' (192.168.1.2). His .conf file is set to listen on port 80. 

How can I see his home directory from my computer? I opened FireFox and tried these:

[http://24.xx.xx.xxx/](http://24.xx.xx.xxx/)
[http://24.xx.xx.xxx/192.168.1.2/](http://24.xx.xx.xxx/192.168.1.2/)
[http://24.xx.xx.xxx/127.0.0.1/](http://24.xx.xx.xxx/127.0.0.1/)
[http://24.xx.xx.xxx/index.html](http://24.xx.xx.xxx/index.html)
[http://24.xx.xx.xxx/index.html:80](http://24.xx.xx.xxx/index.html:80)

...and none of these worked. How do I do this?

Thanks!

Also be aware that many ISPs block port 80 for a household DSL connection.
Perhaps your friend will have to port forward another port than 80, say, 8888 to the port of the internal IP address of the Windows XP box.
That is, on the router, forward anything that hits the router on port 8888 to port 80 of the IP address that the Windows XP box has behind the router.

You'll access it from the internet like this:

[http://public.ip.address.here:8888/](http://public.ip.address.here:8888/)

---

### Post by clay7 on 2008-12-07
That's it! 
I had him forward port 80. When that didn't work, I asked if he had a firewall. Turns out he had ZoneAlarm on. After he shut it down, I could connect!

Many thanks!

---

### Post by happyhacker on 2008-12-08
You should'nt shut down the firewall. Just configure it to allow that access!

---

