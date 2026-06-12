---
title: "Help me understand LXC"
date: 2013-10-11
forum: Virtualisation
---

### Post by The Keeper on 2013-10-11
Okay, so I have LXC installed and have basic containers set up. But I can't really figure out how am I supposed to work with them. All guides stop short of explaining that.

What's the problem then? Once I have the containers set up, I treat them as if they were real computers, as I would do if I were using KVM or Virtualbox for example. But this does not seem to work out, the first hint I get of this is when I try to install mail daemon on a container, port 25 is in use. Obviously same must be true for any service that listens on a port.

I think I'm supposed to use the host's mail daemon to send mails, but I don't understand how. What about logging, should I install cron and logrotate on these containers or write all logs to host and let it worry about logs? I mean, I don't really understand how I should do the things with containers that I normally would do in KVM, Virtualbox or whatever.

Feeling so lost with LXC I'm thinking of using KVM instead...

---

