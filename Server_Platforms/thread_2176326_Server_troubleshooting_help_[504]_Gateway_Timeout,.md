---
title: "Server troubleshooting help: [504] Gateway Timeout, was working server yesterday"
date: 2013-09-23
forum: Server Platforms
---

### Post by theronmuller on 2013-09-23
Two days ago I had a functioning server at [http://mashjournal.zapto.org](http://mashjournal.zapto.org), but on Monday unexplainably the server went down to the outside world. Trying to log in from outside my internal network yields a [504] Gateway Timeout. Pointing a browser to localhost when logged onto the server and pointing a browser at the server's local IP address when logged onto my home network leads to the site loading normally. I'm not sure where to start with troubleshooting this problem and so was hoping for some outside help. Is it the router that I should be checking, or somewhere else?

Any help is much appreciated. Thanks for your time and consideration. I'm looking forward to hearing back.

---

### Post by theronmuller on 2013-09-24
Just a quick update:
This server domain is going through port forwarding, so [http://theronmuller.zapto.org:8080/](http://theronmuller.zapto.org:8080/) points to: [http://mashjournal.zapto.org/](http://mashjournal.zapto.org/) The former address is working but the latter isn't. Perhaps this can help with troubleshooting?

Thanks in advance for any help you may be able to offer.

---

### Post by MeneM on 2013-09-24
This is an interesting setup. We will need to see the config files to understand more. How is one forwarding to the other, and the other proxying for the first?

More info is needed ;-)

---

### Post by SeijiSensei on 2013-09-24
> **theronmuller said:**
> Just a quick update:
This server domain is going through port forwarding, so [http://theronmuller.zapto.org:8080/](http://theronmuller.zapto.org:8080/) points to: [http://mashjournal.zapto.org/](http://mashjournal.zapto.org/)

Usually a port is forwarded to an IP/port combination, not a URL.  On the router, does port 8080 forward back to port 80 on the machine that hosts mashjournal?  If the forward actually uses a hostname rather than an IP, then does the name "mashjournal.zapto.org" point to the IP address of the server on which it is running?  Perhaps a local DNS issue?

Use IP addresses whenever possible for things like port forwards.

---

### Post by theronmuller on 2013-09-29
Thanks for the comments. I'm using no-ip.com's domain management service because I'm running these servers on my home ISP, which issues a dynamically allocated IP address. Changing the configuration for mashjournal.zapto.org on no-ip.com to the server's IP address did the trick.

---

