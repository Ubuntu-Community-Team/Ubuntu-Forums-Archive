---
title: "Simple Web Server Suggestions"
date: 2012-05-19
forum: Server Platforms
---

### Post by codethulhu on 2012-05-19
I'm wanting to setup a simple web server from my home and was wondering what's the best direction to take. I've been using Ubuntu for a few years now and I built my current desktop. The web server will be hosting a simple mostly static site to display information about upcoming events. I would also like to create additional user accounts for trusted people that could SSH into the server to edit things. Opinions on software, hardware, or really anything useful would be greatly appreciated.

---

### Post by MG&amp;TL on 2012-05-19
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") is a good link to get you started.

Your present PC is probably good enough. I have a Pentium IV running as a server, seems to work okay. Good luck!

---

### Post by gordintoronto on 2012-05-20
Does your ISP allow you to run a web server? Do you understand "port forwarding"? How about no-ip or dyndns?

You can get web hosting for as little as $4 a month. If you run a web site, you will need to have your computer running 24/7, running up your electricity bill. For me, this was an easy decision.

Many ISPs allow you to run a web site on their computers, at no additional charge. The web site name is usually something like [www.ispname.com/~username](www.ispname.com/~username)

I have a friend who runs a huge web site (too big to back up on a single DVD) with that kind of name.

---

### Post by LHammonds on 2012-05-20
There are many ways to accomplish what you want...however, letting people SSH into your server to make updates probably isn't the best idea.

Use existing web frameworks such as WordPress, Drupal, or MediaWiki which will allow you to run a nice-looking site and allow other designated people to add / maintain content.

And a previously pointed out, you will also need to decide if you are hosting this on your own PC or on a remote server.  If you host on your own PC, there are many considerations that have to be tackled such as if your ISP gives you a static or dynamic IP (e.g. how will people outside your home find you!), does your ISP allow you to host your own sites (they might actively block certain ports like the web port 80).

There are several places where you can get free hosting but you need to weed through a lot of them in order to find a balance of what features you need and the reliability of the host.  Same goes for any hosts you are looking for pay-for services.

LHammonds

---

