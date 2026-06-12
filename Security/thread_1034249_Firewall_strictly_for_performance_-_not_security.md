---
title: "Firewall strictly for performance - not security?"
date: 2009-01-08
forum: Security
---

### Post by stream303 on 2009-01-08
I have a home system that has no services or ports open for exploitation.  Yet I still run a firewall - since I've been told that it helps to keep the networking hardware from being too chatty about those very closed or unavailable services or ports.

I guess this was the "background noise" that they used to describe it - where your network would still be responding even if you had nothing to exploit - so it was better to run a firewall anyway just to drop the packets altogether.  So even if you have nothing to probe, unless you have a firewall, your network isn't running as fast as it could by being constantly interrupted by random probes, etc.

Was I led down the wrong path?  Does running a firewall solely from a performance standpoint even make any sense?  I guess I haven't seen this angle on firewalls discussed - only security.

I would love any input if I'm totally wasting my time from a performance standpoint.

---

### Post by hyper_ch on 2009-01-08
instant drop of connections will improve speed only a little bit IMHO - except if there are so many concurrent connection that your router/computer can't handle it anymore.. but in that case you have other problems.

---

### Post by Kinstonian on 2009-01-08
There are far better reasons to use a firewall than for a possible performance increase you might get by dropping traffic instead of responding with a RST/ACK.  Keep in mind your computer can send thousands of packets a second...  I think there are a few false assumptions some people make when they say a firewall is useless on Ubuntu...

1.  **Firewalls are only useful for filtering inbound connections**:  If you only look at a firewall as filtering inbound connections, you only see half of it's potential.  What about filtering *outbound* connections with suspicious protocols, or to known bad IPs like the [Russian Business Network](http://en.wikipedia.org/wiki/Russian_Business_Network)?

2.  **All protocols use ports**:  There are protocols like ICMP which don't use ports.  It's not only commonly used for information gathering in attacks, but it's not unreasonable to think history could repeat itself and there could be a vulnerability in the way it's handled by the OS.

3.  **Firewalls are only for preventing attacks**:  While they are no doubt preventative controls, by analyzing the logs they generate they can detect both failed and successful attacks.  If you look at firewall logs from inbound traffic you can detect attacks and take actions.  If you look at firewall logs from outbound traffic like outbound IRC or SMTP traffic to China was blocked, you could have detected a successful attack.

4.  **At no point will there ever be an open port**:  There is a chance that at some point someone could open a port.  Whether it was from the administrator making a mistake in installing/configuring software, or it could be an attacker purposefully using your computer as a server to store and distribute contraband, or perhaps using your computer to host a phishing site.

---

### Post by hyper_ch on 2009-01-08
> **Kinstonian said:**
> I think there are a few false assumptions some people make when they say a firewall is useless on Ubuntu...
Not useless but in most case nothing a desktop user has to worry about.

And to your examples, how would that affect a home user (possibly even one behind a NAT anway)?

By default, ubuntu has no open ports and if one adds a daemon than this person should know how to make sure it won't get abused...

---

### Post by Kinstonian on 2009-01-08
> **hyper_ch said:**
> Not useless but in most case nothing a desktop user has to worry about.

And to your examples, how would that affect a home user (possibly even one behind a NAT anway)?

By default, ubuntu has no open ports and if one adds a daemon than this person should know how to make sure it won't get abused...

I don't see what using a desktop or server has to do with this subject.  Since there are vulnerabilities in both server and client software, both servers and desktops can be compromised...  Yes someone *should* know how to make sure software they install won't get abused, but I'm sure we both know that doesn't always happen for various reasons.

---

### Post by hyper_ch on 2009-01-08
If no daemon is running - which is normally the case on a desktop - then you can't enter the machine ;)

---

### Post by Kinstonian on 2009-01-08
> **hyper_ch said:**
> If no daemon is running - which is normally the case on a desktop - then you can enter the machine ;)

I'm not sure if you meant to say "can**'t** enter the machine" or not.  There are a lot of client side vulnerabilities found in client software such as web browsers, email programs, torrent clients, etc.  If you're using a desktop and someone attacks your client software, you can get hacked even though your computer doesn't offer any services.  That's why many people use NoScript when using FireFox, and keep FF up-to-date.

---

### Post by hyper_ch on 2009-01-08
and how would a firewall prevent an attack on FF?
By design FF must have outgoing and incoming access otherwise it'll be pretty tough browsing the web... this is not a firewall issue here.

And yes, it was a typo. It should say "can't" and I'll correct it.

---

### Post by Kinstonian on 2009-01-08
> **hyper_ch said:**
> and how would a firewall prevent an attack on FF?
By design FF must have outgoing and incoming access otherwise it'll be pretty tough browsing the web... this is not a firewall issue here.

And yes, it was a typo. It should say "can't" and I'll correct it.

I never claimed it would prevent attacks.  It can however mitigate attacks.  For example it might not prevent the actual exploit, but it can mitigate it if your firewall blocks outbound IRC traffic, tries to connect to China, or the Russian Business Newtork, or you can be a good netizen and use the firewall to prevent your computer from scanning and attacking others.

It can also mitigate attacks in the sense that early detection can be prevention.  For example, if you have logging enabled for your firewall and monitor the logs, either manually or something like SWATCH, or OSSEC, you could quickly detect that outbound traffic such as IRC, SMTP, port scan, etc which could indicate you've been compromised, giving you time to respond before the attacker can install a rootkit, get your credit card number, SSN, other passwords, etc.  As they say... prevention is ideal, detection is a must.

---

### Post by hyper_ch on 2009-01-08
and if one gets access to whatever program you can't prevent them to connect to china anyway as this can then be done through proxies or other hijacked computers... a firewall is of no help there...

---

### Post by Kinstonian on 2009-01-08
double post

---

### Post by Kinstonian on 2009-01-08
double post

---

### Post by Kinstonian on 2009-01-08
double post

---

### Post by Kinstonian on 2009-01-08
double post

---

### Post by Kinstonian on 2009-01-08
double post

---

### Post by Kinstonian on 2009-01-08
Edit: double post

---

### Post by stream303 on 2009-01-08
Thanks - good stuff!

I guess you're right that my desktop environment had nothing to do with it.  I was just doing nothing but email and web browsing. No ftp servers or anything like that.

I guess the reason I do run a firewall is that back when I first got DSL service, I was happily running a boxed-set of Red-Hat (remember those?), on a P133 with only 64mb memory. One of the first things I did was to turn OFF the router's firewall.

I thought things were ok, pages loaded, (mostly with lynx back then) but when it came time to download very large files, like installation iso's, the whole thing would take many hours and I could see the speeds going all over the place.  Once I turned the router's firewall back on, downloads were smooth as silk.

My hardware has improved considerably since then, but I got into the habit of using a firewall on default-deny every since, be it in the router, or host-based.

BTW, I *love* UFW!  It is kind of like the porridge that is just right. :)

---

### Post by Kinstonian on 2009-01-08
> **hyper_ch said:**
> and if one gets access to whatever program you can't prevent them to connect to china anyway as this can then be done through proxies or other hijacked computers... a firewall is of no help there...

If you get hacked and are forced to make an outbound connection, there is a pretty decent chance it could be for example, to the Russian Business Network, China, or similar.  That's something worth blocking if possible.  They aren't going to proxy the outbound connection they're using to download their toolkits, or IRC connection, or send SPAM.  Generally attackers use proxies to anonymize themselves, not the victim computers.

Edit: Sorry for all the posts, I was getting proxy errors every time I tried posting, and the results didn't show up until now. :o

---

### Post by hyper_ch on 2009-01-09
if you get hacked you have a lot more to worry about than just outbound connections ;)

---

