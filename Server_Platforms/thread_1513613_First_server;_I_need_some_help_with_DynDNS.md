---
title: "First server; I need some help with DynDNS"
date: 2010-06-19
forum: Server Platforms
---

### Post by Arthur_D on 2010-06-19
Hi folks, I have this machine I signed up for DynDNS. Going to the specific URL just shows the broadband router configuration page. That's a bit peculiar, since going to the server's local IP address I get the suspected test page. I know the IP and URL I signed up are correct, but somehow things gets messed up anyway.

BTW, I'm running ebox on the server for configuration purposes, and I think I got things straight there as well.

Any clues? :confused:

PS: I'll give more details if you need.

---

### Post by CharlesA on 2010-06-19
Have you set the ports to be forwarded? If you point your web browser there, it will try to connect on port 80, which most router web interfaces run on.

Are you trying to connect from inside the network using the dyndns url?

---

### Post by Arthur_D on 2010-06-19
Uh, I don't think so. Seeing the page in ebox -> Firewall -> Port Forwarding; what should be forwarded to where?

Sorry, but as you can tell I'm quite the noob when it comes to this.

---

### Post by CharlesA on 2010-06-19
If it is a web server, you would need to forward port 80.

---

### Post by Arthur_D on 2010-06-19
Hmm, it appears that the firewall module for ebox isn't turned on anyway - so I suppose this isn't the issue then? :confused:

---

### Post by CharlesA on 2010-06-19
Shouldn't be the firewall. You'd need to forward port 80 on the router to whatever IP your web server is running on.

---

### Post by Queue29 on 2010-06-19
>  the broadband router configuration page

Indeed, you need to go through your router's configuration and have it forward port 80 to the local ip of your server. Also, since your router is currently on 80, I would set it to something else first, like 8080 so you can return to it.

---

