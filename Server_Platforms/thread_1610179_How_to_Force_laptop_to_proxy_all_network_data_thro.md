---
title: "How to Force laptop to proxy all network data through SSH.  Know how?"
date: 2010-10-31
forum: Server Platforms
---

### Post by MechaMechanism on 2010-10-31
When I'm on open wifi, also known as public wifi, I want to be secure.  I want to setup my laptop to force all networking to go through SSH.  I mean ALL networking, that means DNS, NTP, the weather applet, web browsers.  In other words, no matter what the laptop does, everything is forced through the SSH tunnel.

I have looked into port forwarding, but that only works on specific programs that you have setup for socks.  I need a program that intercepts all network traffic, so there is no need to go through the hassle of setting up every network using program on an individual level.

I am familiar with socks 5 and polipo.  I don't mind learning squid.  I already tried using Google for this, but it's about setting up specific programs.  I need more than that.


EDIT: Hmm, is this the right sub-forum for this.  Wasn't too sure, it was between security and server or general help.  Feel free to move thread.  I put it in server because of SSH and because I'm asking about using a proxy.

---

### Post by brettg on 2010-11-01
You can't do what you are wanting. If a web server is listening on http (port 80) then you *must* connect to it on port 80.

This cannot be avoided, it is a basic rule of networking.

However, if you have another PC running linux + openssh-server somewhere else, you can *tunnel* all your traffic via that PC over SSH. In that case everything without exception will be encrypted between the two PC's but once it leaves the second PC it will be clear text again on the internet proper.  

See [here for details]("http://tuxnetworks.blogspot.com/2009/09/setting-up-vpn-using-ssh-and-pppd.html") on how to do that.

---

### Post by MechaMechanism on 2010-11-01
This is as close as I can get.  But since this for a netbook, I can setup everything for a socks 5 proxy and just remember to start SSH first.

For web browsing.
[http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/](http://embraceubuntu.com/2006/12/08/ssh-tunnel-socks-proxy-forwarding-secure-browsing/)

For DNS.
[http://www.outflux.net/blog/archives/2006/12/07/paranoid-browsing-with-squid/](http://www.outflux.net/blog/archives/2006/12/07/paranoid-browsing-with-squid/)


I think this thread belongs in security.  The mods might want to move it.

---

### Post by HermanAB on 2010-11-01
Howdy,

Read up on the SSH Socks Proxy feature, the -D parameter.  It is very useful for tunneling a browser.  

This is how I work every day (right now, as I type).  I currently live in a restrictive spot and tunnels all my communications through a server in a another country, using a SSH Socks Proxy.

---

### Post by MechaMechanism on 2010-11-01
> **HermanAB said:**
> Howdy,

Read up on the SSH Socks Proxy feature, the -D parameter.  It is very useful for tunneling a browser.  

This is how I work every day (right now, as I type).  I currently live in a restrictive spot and tunnels all my communications through a server in a another country, using a SSH Socks Proxy.
Thanks for the reply.  I have already started to use it and I am thrilled that I no longer need to forward X.  Using local Firefox is so much faster now.  SSH socks FTW.

---

