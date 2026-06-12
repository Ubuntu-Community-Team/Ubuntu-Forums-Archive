---
title: "DNS Trouble... I think..."
date: 2006-08-09
forum: Server Platforms
---

### Post by JonM1827 on 2006-08-09
I'm having a hard time trying to figure out how to get my box to be accesable externally....

I can go to both [http://localhost;](http://localhost;) my internal ip 192.168.1.100; or my external ip; or to jonmulder.homelinux.com (which i forwarded from dyndns.com to my ip...
(all of that is internal... and it works)

then when i try either the jonmulder.homelinux.com or my external ip address from another computer (off of the network) i get timeout errors...

what do I need to do to fix this issue?

Thanks in advance,
-Jon

Keep in mind that i am very new to both server admin and linux :p

---

### Post by Glut on 2006-08-10
jonmulder.. etc. resolves to 75.3.156.199
If that isn't your ip address, make the appropriate change with dyndns.com, if it is your ip address then your router isn't forwarding port 80 correctly. Take a look at your router's settings.

---

### Post by JonM1827 on 2006-08-10
> **Glut said:**
> jonmulder.. etc. resolves to 75.3.156.199
If that isn't your ip address, make the appropriate change with dyndns.com, if it is your ip address then your router isn't forwarding port 80 correctly. Take a look at your router's settings.

I think I have done all of that stuff correctly, is there anything internally that I need to change... in the configuration files or anything like that for apache that would be affecting this?

Thanks in advance,
-Jon

---

### Post by etechsupport.net on 2006-08-10
There should not be any other problem other than firewall, Bind service and /etc/resolv.conf.

Stop iptables and add proper entry in /etc/resolv.conf and make sure that named service is running on your server. If you can ping to ip addresses outside the server but cannot ping to domains then you need to take a look at all the 3 things I mentioned above.

If this is not sufficient then let me know and I can help you with some routing rules that may sort the problem.

---

### Post by JonM1827 on 2006-08-10
> **etechsupport.net said:**
> There should not be any other problem other than firewall, Bind service and /etc/resolv.conf.

Stop iptables and add proper entry in /etc/resolv.conf and make sure that named service is running on your server. If you can ping to ip addresses outside the server but cannot ping to domains then you need to take a look at all the 3 things I mentioned above.

If this is not sufficient then let me know and I can help you with some routing rules that may sort the problem.

If you could go into a little bit more detail on how to do this it would be great, this is my first attempt at setting up a server.

Thanks again,
-Jon

---

### Post by Glut on 2006-08-10
On the server run: ```
sudo lsof -i|grep apache
``` You should have an entry like ```
apache2 1234 root 3u IPv6 12345 TCP *:www (LISTEN)
``` The important part is the *:www - that tells us that apache is listening for connections on all interfaces. I assume that you're not running a firewall (you're not by default) So then your trouble would be between the outside world and your server. There are 2 possibilities there: your router and your isp. Assuming your isp allows incoming connections on port 80, then the problem is your router.

---

