---
title: "Intrernal port tunneling?"
date: 2011-03-17
forum: Server Platforms
---

### Post by shad0wca7 on 2011-03-17
Hi everyone, this is my first thread on here so please be gentle! I'm also quite new to linux but having a good time with Ubuntu server so far!

As I'm installing things, a lot of them seem to come with their own web interfaces - all accessible through different ports.

Is it possible to configure a page on apache/lighttpd to act as a tunnel to all of these interfaces? So I could open one port and administer all the various programs from a single interface?

For example, open port 80, have a special /config area password protected. When I've accessed that, I can have an html page (I've got no problem doing that) with links to each admin interface - cups, twonky, webmin etc etc but all of those will go through port 80 rather than having to open up all of the individual ports? I hope that makes sense..

Any help would be much appreciated! I've looked into mod_proxy etc but it doesn't seem to be quite what I'm looking for...

---

### Post by rubylaser on 2011-03-17
All you'd have to do to accomplish this is make a simple html page with links to each of your relevant web applications. I'm not sure why you think you'd need a proxy, just create an a href to point to the proper ip and port for each application.  I'd probably suggest running via https (port 445) so your passwords aren't in plain text, and you could use an simple .htaccess file to authenticate your users.

---

### Post by shad0wca7 on 2011-03-17
Wouldn't that just link me to the other service run if on a different port - as the system is behind a router/firewall the request would fail as the port wouldn't be open? Imbtalkijg about accessing the server from another pc outside the network.

---

### Post by rubylaser on 2011-03-17
Yes, outside your LAN, you would need those ports opened up.  There's not a good way that I can think of doing this without either opening the ports up to the outside, or the much safer route is to create the html page, and connect to your home via VPN.

I'm trying to think of how to accomplish what your doing via vhosts, and network trickery, I just can't think of a good way to do this right now other than the afore mentioned options. A proxy won't do what you're wanting, because it would just act like a cache (reverse proxy) for clients.

You could change all of your web based services over to port 80, then use vhosts, and PAT I guess, but a VPN is still easier.

Sorry for the above, I was typing while thinking :)

---

### Post by shad0wca7 on 2011-03-17
Wow, this is a lot tougher than I thought! 

I had noticed webmin has an "http tunnel" feature that looks like it may do what I want but I dont think I can set any bookmarks / have a lost of sites displayed by it. 

Sounds like VPN may be the easiest option at the moment! Thanks

---

### Post by BkkBonanza on 2011-03-18
Actually it's easy. Assuming you have ssh server running for remote access you can connect in on ssh on one open port (by default port 22) and gain access to all your others too. The ssh server includes a secure dynamic (SOCKS) proxy. The command to do it is simple.

From your remote location connect using the -D parameter to create a SOCKS proxy.

ssh -D 8080 myname@myserver

Now port 8080 on your remote machine has a SOCKS5 proxy running on port 8080. So config your browser to use a SOCKS5 proxy on 8080. This is a simple setting in the prefs, network panel. 

In Firefox to make it dead simple to switch normal <-> proxy you can install the QuickProxy add-on. It adds a single button on the status bar to turn on/off proxy mode.

The ssh SOCKS proxy mode is very powerful. It gives you a secure tunnel onto your server that can then access anything else *_as though you were_* on that machine. It will work for email, torrents, etc. as long as they can be told to use a SOCKS proxy.

There are more fancy ways to use this too. eg. if you add -fN to the ssh command then it will start in the background. You would have to kill it manually.

This method is also a great way to secure your communication when on the road since all web access is run thru the encrypted tunnel and appears as though coming from the server. None of your activity is visible on the remote network (except of course the one ssh connection to the server).

---

### Post by shad0wca7 on 2011-03-18
Thanks for the advice, whilst not quite as seamless as I was hoping, it should still prove very useful!

---

### Post by BkkBonanza on 2011-03-18
It would be nice if someone made a simple Firefox add-on to start run the ssh command and then set the proxy setting. I haven't seen one for that yet. Maybe I should look at a small mod to the QuickProxy one to do that. Would make it a one-click affair.

---

### Post by rubylaser on 2011-03-18
This is a great idea, I don't why ssh didn't come to my mind, but I'm very glad that BkkBonanza spoke up.

---

### Post by shad0wca7 on 2011-03-18
Marked this as solved as you gave some good options, thanks :)

---

