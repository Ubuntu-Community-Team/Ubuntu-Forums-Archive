---
title: "secure a SMTP server"
date: 2017-08-05
forum: Server Platforms
---

### Post by cazz on 2017-08-05
is it possible to secure so you can just sent to a specific domain.
I use Postfix on one server to send log to a email account. The sender and reciver is save domain.
But I like to have it on more of my server but I'm afraid that someone is going to use to send spam.

---

### Post by TheFu on 2017-08-05
Sure. You can block all ports to all domains everywhere, then allow 1 port to 1 specific location, if you like.
That will break all sorts of things, but you can do it.  Do this with firewall rules.

If you want to not be a spam-relay, don't allow inbound connections over any interface that is available to the internet - or just listen on the localhost interface only.  There is an interface setting for this.  If someone breaks into your machine, they will be able to spam.  If you configure as a "leaf node", then it won't accept non-local email.

BTW, all of this is outlined in the different postfix manpages.  They are pretty good and worth a read, even if you don't understand everything now.  Every week, you'll learn a little more and a little more.

There are free spam-relay testing services on the internet. Anyone who hacks into the system can certainly drop a little email script onto it and start spamming without using postfix at all.  And a host-only firewall wouldn't stop them from turning off the outbound email rule and spamming the world too.  That really needs to be controlled at the WAN firewall, IMHO. But having an extra hoop on the host in a firewall rule can't hurt.

I think there are a few confusing typos in the question.

---

### Post by cazz on 2017-08-05
Sorry about that, english is not my first language and I sometime write strange when I'm in a hurry.

hmm that is true, I can do something with the firewall rules
mmm have to read a little more about this.
Some of the system I have on my linux computers can send mail log when it have done something and is good if I want to see what happend.

---

