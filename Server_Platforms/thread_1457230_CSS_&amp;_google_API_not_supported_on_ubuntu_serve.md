---
title: "CSS &amp; google API not supported on ubuntu server?"
date: 2010-04-18
forum: Server Platforms
---

### Post by ingenuitylabs on 2010-04-18
I'm hoping someone will assist me here, as I've searched relentlessly with no luck.

I have ubuntu server installed and working great.  I'm using ehcp to configure everything.

Everything seems to be working great, except that CSS doesn't seem to be working on my server and there is a problem communicating with the google API.

Here is an example, this site is hosted at godaddy:

[http://acabinbythestream.com](http://acabinbythestream.com)

This site is hosted on my server:

[http://acabinbythestream.net](http://acabinbythestream.net)

The directions tab displays a map using the google API.  On the godaddy server (.com) it works fine, but does not on my server (.net)

As I said I've tried to find the answers to these problems but with no luck, if somone could even point me in the right direction it would be greatly appreciated.

thx!

---

### Post by wojox on 2010-04-18
I can't even get your site to load.

---

### Post by ingenuitylabs on 2010-04-18
:(

So I'm guessing that it has something to do with localhost?  I can access it from every computer on the network here, but how can test to see if I can connect from outside my LAN?  A proxy?  I tried this before and couldn't get it to work.

Sorry for the noobness, this is the first time (i thought) that I had this server working.

Well I made some changes in the router that I'm hoping worked.  I can ping the domain names and my ip address with success.

I used DMZ port forwarding but I'm not sure this was a good idea.
---

So if i traceroute, the domain resolves to my ip no problems, but when i goto say unhideit.com and try to access it via proxy it will not.  I've tried changing the ports on my router, i've disabled the router's firewall and still not working :(  arghhh   I can SSH and FTP from here no problems, but seems not from the outside world.  Any suggestions?

---

### Post by ingenuitylabs on 2010-04-18
I'm stumped.

When I traceroute the domain name (not in hosts file) it resolves to my IP address no problem, but I cannot access the websites outside the LAN.

Anyone please tell me what I'm doing wrong?

---

### Post by spynappels on 2010-04-19
Let me just check a few things here.

1. You have port 80 opened on your router and forwarded to the server which hosts your site?

2. Your ISP does not block port 80? (Very many do for domestic accounts)

3. You have set up a firewall rule to allow TCP traffice on Port 80 from all sources to pass through to your LAN, and more specifically to your server?

---

### Post by lisati on 2010-04-19
> **spynappels said:**
> Let me just check a few things here.

1. You have port 80 opened on your router and forwarded to the server which hosts your site?

2. Your ISP does not block port 80? (Very many do for domestic accounts)

3. You have set up a firewall rule to allow TCP traffice on Port 80 from all sources to pass through to your LAN, and more specifically to your server?

4. If you're using a dynamic IP address, have you updated the relevant DNS records?

---

### Post by ingenuitylabs on 2010-04-20
Ok I solved the problem of no outside access.

Apparently my ISP was blocking port 80 despite the commercial account.  Now that that is resolved I can access my server from outside the LAN here.

The problem with the google API and CSS is still occurring, despite a reinstall of Ubuntu server and ehcp.

My question, is there something i must install to support CSS and communication with the google API?

The website is here:

[http://acabinbythestream.net](http://acabinbythestream.net)

you will see that the directions tab returns an error whereas on the site hosted at godaddy:

[http://acabinbythestream.com](http://acabinbythestream.com) 

it works fine.

Any help would be greatly appreciated!

*EDIT:  I am no longer user a dynamic ip service...i was briefly after finding out that port 80 was blocked so that i could use 8080 temporarily, but now that port 80 has been unblocked there is no dynamic name service at all.

Ok I believe I've figured out why I cannot communicate with the google API.  I'm sure I need to update the key used in the (.net) version vs. the (.com) version.  Going to try that now, but still have no clue why CSS is not working.

---

### Post by ingenuitylabs on 2010-04-20
Ok i have CSS working, actually not sure why it wasn't in the first place, but now it is :confused:

As for the google API problem...I got a new key for the (.net) version of the website and incorporated it into the actionscript package that I created to originally use on the (.com) version, but no success.

The key is updated, but the API still fails.

I've accessed my site using an http proxy so that I can test it outside my LAN, but this seems to create more problems as the .swf doesn't even seem to load on the directions tab this way.

Can anyone tell me what is the best method of accessing my server from outside my LAN?  I cannot imagine that an http proxy(like proxy.org) is the best method, but I don't want to go screwing with my hosts file either b/c i always seem to break something when i do.

---

### Post by ingenuitylabs on 2010-04-22
Well if it helps anyone in the future I've figured out all these problems.

The last problem with the google API was a result of an update to the API by google.  The new key didn't work with the previous code, so I rewrote and recompiled the .swf for the (.net) version and all is fine now.

I am a complete newbie to linux and servers in general, so I'm now moving on to learn how to properly maintain my server and make sure it's secure.

Currently I'm puzzled by a [debug] mode_deflate.c(615): [client..] error in my error.log.  I'm having a bit of trouble finding any info. on this on the web, so off to do more googling.... :popcorn:

---

