---
title: "Multiple forums on apache2"
date: 2009-10-28
forum: Server Platforms
---

### Post by weryl on 2009-10-28
Hi all,

I setup a LAMP server about 2 years ago and its been working great since then. Now it's running ubuntu 9.04 with no problem whatsoever and I want to upgrade the web server.

I wrote a few forums from scratch in php and I'm currently hosting two of them, but I'd like to create 1-2 more (and many more in the future). They all use the same address except for the last part:

[http://my.server.net/forum1](http://my.server.net/forum1)
[http://my.server.net/forum2](http://my.server.net/forum2)

What ive recently realized is that the web browser saves only one session and password for everything under "my.server.net", so logging in to a second server logs you out of the first (session gets overriden (sry if wrong spelling)). Also, you never know which password is gonna appear by default if you tell the browser to remember it, which is a pain.

So i thought about it and i came up with the following options, which i'd like you to comment and/or propose additional ones:

1. Group every forum under the same structure (i.e. my.server.net/forums), with a single login, and customized access. For example Mike might have access to forum 1, but not forum 2. Seems like an easy but efficient solution..

2. Create virtual hosts with different addresses. I don't know much about this one but i thought it might be a good idea if i keep increasing the number of web pages over the years. Does it seem appropriate for my problem?

3. ???

4. Profit

Hum i thought i had more options when i went to sleep yesterday, shouldn't have waited until morning to post. Please give me your thoughts on this, and thanx in advance.

---

### Post by bgeraghty on 2009-10-28
#1 Sounds simple, depending how large the forums are and how much user/group security detail you want to take on..

Apart from just splitting the forums to separate machines, the idea with virtual hosts might work, getting the point across to the browser that the individual forums are supposed to be separate scripts. Is it possible to change how the script maintains sessions slightly for each forum so they have some level of uniqueness? Such as changing how each forum cookies it's users?

---

### Post by i.r.id10t on 2009-10-28
Vhosts are your solution.  You may want to look at ISPConfig since it allows you to add new domains and sites very easily, as well as database usage, etc.

---

### Post by weryl on 2009-10-28
> **bgeraghty said:**
> #1 Sounds simple, depending how large the forums are and how much user/group security detail you want to take on..

Apart from just splitting the forums to separate machines, the idea with virtual hosts might work, getting the point across to the browser that the individual forums are supposed to be separate scripts. Is it possible to change how the script maintains sessions slightly for each forum so they have some level of uniqueness? Such as changing how each forum cookies it's users?

I didn't set up any cookie in the script, just a session with the forum title (unique to each), the username and I think that's it. If I understand well though, the browser still saves a cookie for the session, and the first one gets dumped when the second one is created. How can I prevent that? Do I need to set up cookies manually instead of letting session_start() do it?

---

### Post by weryl on 2009-10-28
> **i.r.id10t said:**
> Vhosts are your solution.  You may want to look at ISPConfig since it allows you to add new domains and sites very easily, as well as database usage, etc.

ISPConfig? Is this for apache? Sry I'm on my phone so I can't make a good research until I get back home..

---

### Post by Lars Noodén on 2009-10-28
If you want both forums tightly lock-stepped then putting them together under the same package will work.  

Otherwise, take a look at [virtual hosts](http://httpd.apache.org/docs/2.0/vhosts/name-based.html) (aka vhosts), probably name-based ones.  Using a vhost makes it very easy to move the whole service around from machine to machine as well as to keep customizations and upgrades separate.  

You can even set up an extra vhost per forum to use to test out patches or changes before inflicting them on a live audience.

---

### Post by weryl on 2009-10-28
Thanx alot, I decided to set up named virtual hosts and its working great! I thought it would be harder but it was quite easy, i'm almost disappointed :p

---

### Post by Vegan on 2009-10-29
i use several named hosts, and many have phpBB and other tools. I posted a piece on my site for those interested in the manual method to set them up.

---

