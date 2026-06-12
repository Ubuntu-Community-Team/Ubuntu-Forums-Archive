---
title: "Adding a domainname to my webserver"
date: 2012-05-18
forum: Server Platforms
---

### Post by youngroger on 2012-05-18
Hi,

As i'm new to Ubuntu server, my guess is that this isn't a really `smart` question, but I'm a bit confused. I've set up a webserver with LAMP on my old computer and I'm able to access it trough my external IP address all over the world. As I used to host my website on just another webhosting company I bought a domainname over there. But now I want to assign the domainname to my personal webserver, but I'm totally confused how to go there. I've read articles on DNS etcetera, making me think that I should run my own DNS server or...? I have no clue actually, I would be very thankfull if somebody could help me out!

~youngroger

---

### Post by Cheesemill on 2012-05-19
No need to run your own DNS, that just complicates things.

All you need to do is log on to the control panel of your webhosting company and edit the A record of your domain name in the DNS settings so that it points to your IP.

I can't talk you through it exactly as hosting companies use different methods of doing this. There should be more info or a help section on the webhosts site to point you in the right direction.

---

### Post by CharlesA on 2012-05-19
The easiest way is to just create an A (Host) record in your webhost's DNS control panel and point your domain name to your external IP.

You would have to ensure you have port forwarding setup, which looks like you have already done.

---

