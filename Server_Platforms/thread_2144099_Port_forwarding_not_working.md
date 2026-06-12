---
title: "Port forwarding not working"
date: 2013-05-11
forum: Server Platforms
---

### Post by crabhunter on 2013-05-11
Hi, although I have setup port forwarding (Port 80) on my router when I try to access my server from the www I just get my routers login page.
Are there any other settings I need to change in the router? I am trying to route port 80 traffic to 192.168.1.140
To test it I have got my ip from whatismyip.com and typed that into another pc on the local network.
That results in the routers login page.
I can reach my server from other pcs on the network by using 192.168.1.140
Mike

---

### Post by lisati on 2013-05-11
Hello world?

---

### Post by darkod on 2013-05-11
If by local network you mean your home network, most home routers will not be able to send the traffic back when you are trying from inside the same home network.

But if you tried from the outside, it should have worked. Make sure the router firewall is not blocking port 80, and also if the router has the option to disable external (public) login, do it. It's a good thing to have is disabled anyway since people might try to break into your router if it's admin page is open to the world.

Also you can simply mode the admin page to another port, like 8080. Then it will not interfere with 80.

---

### Post by crabhunter on 2013-05-11
Well what do you know, it is working.
Just tried from my phone with wi-fi turned off and I get right through to my webpage.
Thanks darkod.
Mike

---

