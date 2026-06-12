---
title: "Set Up Local SSH SOCKS5 Tunnel"
date: 2010-06-11
forum: Security
---

### Post by SlidingHorn on 2010-06-11
This is probably a very stupid question, but I don't mind looking like an idiot from time to time.

I was looking at [this thread]("http://ubuntuforums.org/showthread.php?t=650368"), and the idea posed seemed interesting to me.  As my neighbor & I share an unsecured connection (their choice, not mine) because we're cheap, and I want to protect my information.

> If you are connecting from a Mac or Linux machine try put this

ssh -D 7070 username@server

or if you run ssh on a non-standard port

ssh -p 443 -D 7070 username@server

This creates a LOCAL socks 5 proxy (effectively) through the tunnel, just set your browser (or whatever) to use socks 5 proxy 127.0.0.1:7070

No need for squid.

Here's the dumb question...if I have openSSH/apache etc installed, shouldn't I be able to do this by <username>@127.0.0.1?  If I need to do it through a remote server, is there a free service out there that I could use?

I ask because if I try setting this up through localhost (via ip or name), my ip doesn't change if I check it on a site like whatismyip.  As always, any help you could provide is greatly appreciated! :)

---

### Post by bodhi.zazen on 2010-06-11
You need a remote host.

If you ssh to local host you will create a socks socket, and the traffic from firefox to localhost will be encrypted, but when localhost makes the request for you no more encryption.

FYI - you have a client, you ssh to a server and makes a socks tunnel ...

Traffic from your client is encrypted to your server. This is helpful if you want privacy on an unsecured network , but requires a remote host.

In your case it is harder, I suggest you either decide to trust your neighbor or get your own internet connection. 

You will have to decide it you trust your neighbor enough to justify the cost savings.

---

### Post by SlidingHorn on 2010-06-11
I'd hate to use up the resources/bandwidth, but would I be able to do this through a VPS I have?

---

### Post by bodhi.zazen on 2010-06-11
> **SlidingHorn said:**
> I'd hate to use up the resources/bandwidth, but would I be able to do this through a VPS I have?

If you vps has a ssh server, yes.

Depending on what you do, it should not eat up *that* much bandwidth, just do not DL large files through the tunnel.

---

### Post by SlidingHorn on 2010-06-11
cool...I'll hook it up through there, then.

It's not that I don't trust my neighbors -- they aren't tech savvy enough to do anything malicious or harmful to my computer.  I also use unsecured wifi networks @ coffee shops, libraries, etc that I'd like to avoid any prying eyes...

Thanks for your help!  I'll mark the thread solved once I get it set up on my server (not going to try tonight though)

---

### Post by bodhi.zazen on 2010-06-11
OK, if you need help ask. The process is very straight forward.

The biggest concern is that you secure your ssh server. I advise you use keys , disable password logins, and take a look at a service such as denyhosts.

---

