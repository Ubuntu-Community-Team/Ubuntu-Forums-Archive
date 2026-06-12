---
title: "Jabber Server with MSN Transport"
date: 2009-05-17
forum: Server Platforms
---

### Post by Zeromaru on 2009-05-17
I've done a lot of research on this topic, and to date I've not found any instructions on setting up a Jabber Server with MSN Transport for the average user. My primary computer is a Macbook, and I have an Ubuntu server configured to be (mostly) exposed to the internet.

What I want is a way to chat with Windows Live contacts in iChat. I extremely dislike every other IM client available for OS X and everyone I know uses Windows Live. The best way to do this is a Jabber server with an MSN transport. Setting the server up locally would be ideal, but I don't have the knowledge to do this myself and no-one is interested in using Windows Live on Mac so I can't get help on the matter (plus for some reason Adium is universally loved and saying one doesn't like it never goes well).

What I don't want is to use some third-party server. Namely, I don't want my username/password stored there.

I have a server running Ubuntu already exposing a number of services that I can access from both while I'm home and while away, using No-IP's free dynamic DNS server. I've found a guide [here]("http://www.debian-administration.org/articles/392") that would seem to work, however it requires using extra subdomains that I can't make, and I can't figure out how to properly modify it to work.

Long and short: is there any guides around on setting up Jabber on a home server, to be accessed from both home and away, with an MSN transport? With some detail on which ports need forwarding?

---

### Post by localhorse on 2009-06-23
If I'm not mistaken, those subdomains you are referring to are only necessary internally for the server to talk to each separate component. So you should be able to just put those names in your /etc/hosts file, pointing to 127.0.0.1 - I've done this before with ejabberd.

So, just make sure that your dynamic domain is pointing to the right address, and that you have ports 5222 and 5223 (might want to check Google, this is just from memory) open, and it should work fine for you.

Let me know if you have any questions. I may not have been clear about what I meant about the subdomains. It won't be anything to do with your dynamic DNS name, these are names that you can just make up, since they won't be used outside your LAN, like your dynamic domain name.

---

