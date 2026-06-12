---
title: "load balance across multiple sites? is that a good idea?"
date: 2010-06-14
forum: Server Platforms
---

### Post by mattkoehn on 2010-06-14
I'm looking for advice if this is the proper way to setup a server, given I've run out of knowledge where I'm looking to go. I've setup subsonic, which is a free music streaming application on Ubuntu. I'm looking to get more **upload bandwidth**.

So my thought was to set up a **ubuntu cloud**, ditch a few boxes at a few different places and hope rely on the network load balancing. However I've been unable to figure out if this would work across big distances, if the server would load balance simple applications like the subonic server, or if there isn't a better way to go about this. Please advise with how I should be rolling this out or if this is a good idea. Thank you for reading.

---

### Post by stmiller on 2010-06-14
What is your current hosting company? Just go to one where you can get more bandwidth.

A couple of the big cloud hosting companies are:

[http://www.gogrid.com](http://www.gogrid.com)

[http://www.linode.com](http://www.linode.com)

---

### Post by mattkoehn on 2010-06-14
I'm just running it off a box in my apartment. I see what you mean though. Most people wouldn't go through the hassle of setting up boxes at multiple sites, they would just pay for hosting. I guess I need to figure out if I want to throw money at this or not. Currently all free you understand. Thats why I was going the route of more boxes at more sites.

---

### Post by HermanAB on 2010-06-15
The simplest solution is rsync and Round Robin DNS.

---

### Post by mattkoehn on 2010-06-15
The round robin with rsync is sort of what I had in my head with the cloud idea, but clearly more simple. It was just hard to ascertain the best practices by googling buzz words. Well I've got a lot to go on. It does seem like I have to either pay for hosting or do a round robin. Thank you.

---

