---
title: "Why is UFW disabled by default?"
date: 2023-08-07
forum: Security
---

### Post by BBQdave on 2023-08-07
My home network has built in firewall and other security services, so I'm not as concerned with individual computers and firewalls at home.

However, I was traveling this past week and was on other networks. Checked firewall settings, and by default it is off. Easy enough to enable firewall, and was good to go for travels.

Why is UFW disabled? Is there other security functions and/or firewall functions active by default? Are there security functions at the kernel level, so no need for firewall or UFW?

Curious about the basic security of a default Ubuntu install, thanks :)

---

### Post by The Cog on 2023-08-08
There is generally no reason to enable a firewall on a default Linux install. Unlike Windows which has many running services listening for incoming connections that cannot be stopped, Linux has very few - I can think of one: avahi-daemon which is a network discovery name service. 
Any other listening services will be those that you chose you install yourself, and presumably therefore want to be available to accept connections. A firewall blocking access to those services would just create lots of complaints that the newly installed service isn't working. 
Many services you might install (like databases and web servers) only listen on the loopback by default so are only accessible from the local machine, and need explicit configuration changes if you want them to accept connections from outside. We get enough support requests about those not working properly. 

Think about it - what do you want the firewall to block? Why have you installed that service and configured it to listen for external connections if you want to block access to it? It only really makes sense if you want to be selective about which ranges of IP addresses you want to allow to connect, e.g. allow only local network addresses to use the service, or block specific ranges for some reason, like foreign countries.

---

### Post by BBQdave on 2023-08-08
Thanks for the information The Cog :) I'm probably not up to date with my thoughts on firewalls, but if you are on a public network or unknown (not controlled by you) home network - would a firewall help with unwanted incoming connections?

To my understanding, the firewall allows out going connections (initiated by you or a service on your computer) and denies incoming connections not initiated by you.

I have a simple workstation set up with Ubuntu 22.04 and firewall enabled. So far, all is functioning well - traveling and at home on my own network.

Thanks again for the information.

---

### Post by Rubi1200 on 2023-08-08
This sticky at the top of the forum has some great information worth reading:
[https://ubuntuforums.org/showthread.php?t=1871177](https://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by BBQdave on 2023-08-08
Thank you Rubi1200 :)

Good information and links to explore deeper into the subject.

---

### Post by donald187 on 2023-08-11
You might get a kick out of this site.  Shields Up! by security expert Steve Gibson will probe the ports on your computer to see if they are open, closed, or stealth.  You could test with and without a firewall to compare.

[URL="https://www.grc.com/shieldsup"]https://www.grc.com/shieldsup

[https://en.wikipedia.org/wiki/Steve_Gibson_(computer_programmer)](https://en.wikipedia.org/wiki/Steve_Gibson_(computer_programmer))
[/URL]

---

