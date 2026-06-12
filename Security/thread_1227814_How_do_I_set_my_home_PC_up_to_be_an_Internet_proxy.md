---
title: "How do I set my home PC up to be an Internet proxy via SSH?"
date: 2009-07-31
forum: Security
---

### Post by diablo75 on 2009-07-31
I am currently outside the US and am having to pay an ISP 60 dollars a month for low bandwidth access to the Internet, which also happened to be filtered for certain websites.  I'd like my browsing to be private over this network and for it to be able to access all that I am able to access from home back in the states.

Currently I have my router at home using dyndns and port-forwarding to make accessing my PC at home a snap.  I have SSH running on my home PC and will use it to occasionally make file transfers between home and here easy.  I want to be able to set my home PC up to act as a proxy for Internet activity so I don't have to worry about the immediate ISP (here) blocking or easily observing my browsing.

---

### Post by noway2 on 2009-07-31
You can use a SOCKS proxy.  If you are using Firefox, get the addon Foxy Proxy and configure a socks proxy for your home server.

You can then SSH into your home server as follows.  Assuming you set the SOCKS proxy to port 9999, use ssh -ND 9999 user@yourserver.  This will aslo work with RSA key authentication just use ssh -ND 9999.

I suggest using Firefox because it has the ability to do the DNS searching remotely also.  Go into about:config, search for DNS and set remote DNS to true.  This will then use your server instead of the local provider for looking up your queries.  As your traffic will be encrypted by the SSH tunnel, you should be quite secure and private.

This works well for anywhere you want to be private, such as a wifi hotspot.

---

### Post by diablo75 on 2009-07-31
> **noway2 said:**
> You can use a SOCKS proxy.  If you are using Firefox, get the addon Foxy Proxy and configure a socks proxy for your home server.

I'm pretty clueless when it comes to this stuff so I need a little extra help.

You say "get the addon Foxy Proxy...for your home server."  Does this mean:  Install Foxy Proxy in firefox on my home PC, or do you mean install it on my laptop here out of the country and configure it to use port 9999 (or whatever the ssh port I specify) to access the Internet?  If it's the latter, do I have to do anything at all on my home PC before doing this?

My best understanding right now is:

1.  Install Foxy Proxy on my laptop.
2.  Run the ssh -ND port# command on the laptop to access the home PC.
3.  Configure Foxy Proxy to use the port# in the above command.
4.  Browse the web. 

I'm sure I'm leaving steps out because I don't know anything about SOCKS...

---

### Post by kevdog on 2009-07-31
Here is a tutorial:

[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by diablo75 on 2009-08-01
Fantastic.  It works!

I have more questions related to this for other apps but I'll start other threads for that when I have time.  Thank a lot for the tutorial link; it was quite easy (I love simplicity).

---

### Post by diablo75 on 2009-08-01
It works.  But now I'm wondering....

Is it possible to configure the entire system to use this proxy for anything Internet related, instead of entering these settings into individual applications one after another?

---

### Post by Dr Small on 2009-08-01
> **diablo75 said:**
> It works.  But now I'm wondering....

Is it possible to configure the entire system to use this proxy for anything Internet related, instead of entering these settings into individual applications one after another?
That's where this tutorial plays in:
[http://ubuntuforums.org/showthread.php?t=1078033](http://ubuntuforums.org/showthread.php?t=1078033)

Basically, you can skip the Dansguardian and Squid stuff, and just focus on setting up Privoxy (configuring it to use your SOCKS proxy to your SSH server) and using Transproxy (the init.d shell script).

Transproxy just uses iptables to forward requests to Privoxy which forwards requests directly to your SOCKS proxy. It shouldn't be that difficult to setup.

---

### Post by kevdog on 2009-08-01
Dr. Small

I didn't know about that method -- but that's pretty neat.

Of course you could just set yourself up a VPN (OpenVPN) -- and this of course would forward all connections encrypted between the host and client (considering of course that its configured correctly).

---

### Post by Dr Small on 2009-08-01
> **kevdog said:**
> Dr. Small

I didn't know about that method -- but that's pretty neat.

Of course you could just set yourself up a VPN (OpenVPN) -- and this of course would forward all connections encrypted between the host and client (considering of course that its configured correctly).
Yes, that's another way, too. But I've never had the priviledge nor fast enough speeds to be able to setup a VPN, so I just do it the old fashioned way, lol ;)

---

### Post by The Cog on 2009-08-02
Another way:
On your home PC, run tinyptoxy (it's in the repositories), listening on, say, port 8080. Do NOT forward ports from the internte to this proxy.

Then use SSH to tunnel to it like this:
ssh -L127.0.0.1:8080:127.0.0.1:8080 [email]username@my.home.addres[/email]s
Now your local machine is effectively a proxy. Any connection to your machine gets forwarded to the proxy at home. Configure firefox to use 127.0.0.1 port 8080 as its proxy. To update Ubuntu, do:
$ export http_proxy=http://127.0.0.1:8080/
$ sudo aptitude update
$ sudo aptitude upgrade

You can even open this up a bit and allow other local machines to use yours as a proxy. Use this SSH command:
EDIT: Correction:
ssh -L0.0.0.0:8080:127.0.0.1:8080 [email]username@my.home.addres[/email]s
and your PC will act as a proxy for your whole local LAN - the SSH tunnel is accepting connections to any local IP address on the PC.

I somethimes use this method at work to update or install software on servers that don't have direct internet access.

---

