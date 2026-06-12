---
title: "IP Cam problems accessing locally by external ip"
date: 2012-02-14
forum: The Cafe
---

### Post by steveodeevo on 2012-02-14
Hello,

I bought and setup an ip cam today, which uses no-ip and is updated by my ubuntu desktop, the thing works perfectly now finally, as after an hour or so of playing with the router, firewall, dmz, and virtual servers, and upnp, and other settings and scratching my head as to why  I could not see it whenever I typed my external ip into my browser, I tried access it from an ssh tunnel from my server on the internet and it appeared.

So I am a bit confused by this, in my experience opening the dmz and pointing it to the server or web server or using a virtual server setting in the router should allow you to use your external ip address to see the server on a local machine.

The webcam uses port 80 to share its image and controls on, so upnp and so on is not really needed, just a simple port redirect on port 80 to the ip address of the camera.

And as I found out after a while of trying, the outside world could indeed see my camera, it seems it is just me locally that can't using my external ip address!

I have used this setup before to access apache and used the external ip and it worked fine, so as you can imagine I am sat here wondering why it didn't work in this case?

The best I can think of is that my belkin router has some built in setting I can not change which blocks connections from with in my network back to itself, or that nat was somehow breaking it!

Anyway thought I would chuck it out there to see if anyone has any idea why it would do it, and hell someone else might be sat there scratching their head as to why theirs doesn't work and read this and think, ah try it on another connection (mobile phone, shh tunnel, second line etc), sounds stupid but if I had done that at the start I would not have wasted an hour flipping the switches in the router wondering why I could not see the damn thing!

Incidently the setup of the no-ip client on ubuntu was a breeze with a simple **sudo apt-get install no-ip** and follow on screen instructions (enter username, password, host to update)!

You can view the camera on my website at [http://www.stephen-phillips.co.uk/webcam.html](http://www.stephen-phillips.co.uk/webcam.html) or login and control it as an operator at [http://southdevonweb.no-ip.biz](http://southdevonweb.no-ip.biz) (username **guest** with no password) though all you will see is my messy room most of the time!

---

### Post by robsoles on 2012-02-14
All the routers that I have ever tried any simile of that with have simply blocked (or failed to allow) such connections.


I disabled their web interfaces, I changed their web interface port numbers and I hacked away at a couple - it is probable that to allow that the manufacturers would have to break something about their firewall.

---

### Post by steveodeevo on 2012-02-17
Oddly enough my old ZyXel router had support for services like No-Ip built right into the web admin, which made hosting servers a breeze, as it would even update the External IP from the router automatically, the build quality was a bit poor however and the aerial snapped off!

---

### Post by robsoles on 2012-02-17
All the routers I have owned have had "dyndns.org" updating capabilities for peope trying to run services from dynamically assigned IP addresses. Even my Cable 3.0 modem has a "Dynamic DNS" section where this can be set up.

All my modems have included that functionality and if any of them was capable of allowing internal-to-internal connections by using the public IP address then it was the first of two D-Link modems I used on ADSL2+. Mind you, I ditched that D-Link because it persistently connected using ADSL(standard) instead and a loan Netgear hooked straight in at a much higher speed using ADSL2+

It happens that I have DNS servers both at home and on my VPS, they are both configured with only public addresses and they are public - the home one is master and pushes it's records to the slave on the VPS.

The services on my home network that I always refer to have a public address on the worldwideweb and that public address is returned by my DNS and then, as discussed in this thread, my modem/router does not allow me to connect to it at home - I just enter each of my local services into the hosts file of each local computer I might use said service from but I don't record the same address as my domain name servers are dishing out (that wouldn't fix it for me), I enter the local IP address instead.

If my LAN were based at 10.25.50.0/8 then my hosts file could end up looking like this;```
10.25.50.12    home.robs-example.com
10.25.50.17    ns1.robs-example.com
10.25.50.12    mail.robs-example.com
```so I can just type their names and use them as I would from a computer outside of my local area network.

---

### Post by CharlesA on 2012-02-17
The problem is not no-ip, it is that most routers do not allow loopback connections - using your external IP from inside your local network.

You can either add an entry in a local dns server if you have one, or add it to the hosts file as robsoles suggested to point that URL to the local IP.

---

### Post by FuturePilot on 2012-02-17
[LIST=1]
[*]Putting yourself in a DMZ is a really bad idea unless you know what you're doing. You only need to forward the one port that it runs on to your computer.
[*]The reason you cannot access your public IP from inside your network is probably a NAT Redirection problem. Check your router if there is a setting for this.
[/LIST]

---

