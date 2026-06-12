---
title: "Can't access web server from LAN"
date: 2007-03-22
forum: Server Platforms
---

### Post by dfreer on 2007-03-22
Hi everyone,

My website is accessible from the internet by name ([http://www.dfreer.org)](http://www.dfreer.org)), but not from my LAN. It was suggested that it is a router problem, but I'm pretty sure I do not have my web server configured correctly. I have a static IP address (66.209.138.18 ), and my web server is behind a Netgear Wireless Router WGR614v6. When I ping the website from my LAN, I get a response:

```
64 bytes from stm-ftth-1189.brightohio.net (66.209.138.18): icmp_seq=1 ttl=64 time=0.622 ms
```

When I ping my website from the internet:

```
PING dfreer.org (66.209.138.18) 56(84) bytes of data.
4 packets transmitted, 0 received, 100% packet loss, time 3009ms
```

DNS Reverse Lookup from internet:

```
You are coming from IP address  66.209.138.18 using port 49916.
A DNS reverse lookup shows your hostname as stm-ftth-1189.brightohio.net.
```

When I use freeproxy.ca to look at my webpage from the internet, I can see my home page. Weird thing is, when I look at [http://stm-ftth-1189.brightohio.net](http://stm-ftth-1189.brightohio.net) from freeproxy.ca I can see my homepage... but again, if I use [http://stm-ftth-1189.brightohio.net](http://stm-ftth-1189.brightohio.net) from my LAN nothing happens. Can anyone please help me out here?

---

### Post by conjur3r on 2007-03-22
What happens when you ping the internal IP address of the server and also what happens when you point your browser to the internal IP address?

---

### Post by dfreer on 2007-03-22
Sorry, forgot to mention that. I can access the website from the LAN using IP address and ping it too. I just can't access it using the Domain name, which is what this thread is  for.

---

### Post by scxtt on 2007-03-22
that's normal - and really what difference does it make?  you'll see the same thing if you do http://<local ip>/ vs. http://<outside ip>/ -- so why fuss about it? ( i'm curious more than condemning you :) ) - i used to wonder about it too, back when i tried to use my external IP to view my website ... i just learned to live w/:

internal ip : when w/in network
external ip : when outside network

on a weird side note, i use homedns.org for DNS lookups for my modem IP - and i can point to it w/ any browser and get to it ... same router, same everything (well different ISP) but i'm using homedns.org ...

---

### Post by MJN on 2007-03-22
> **scxtt said:**
> that's normal - and really what difference does it make?
 
Whilst it is relatively common it's not 'normal' as far as being acceptable/necessary is concerned, and indeed it can make a massive difference! Other than that I agree! ;)
 
The cause is due to some home routers not supporting so-called 'NAT loopback' (see [http://www.dyndns.com/support/kb/loopback_connections.html](http://www.dyndns.com/support/kb/loopback_connections.html) for one of many descriptions). It's down to the poor feature implementation of the NAT in these routers thanks to them being designed/built to a cost.
 
The real problem comes from when you want to use name based virtual hosting - accessing by IP address will not work. The only solution is to have an internal DNS (or hosts files on each machine) that translates your URLs to internal addresses as opposed to the external addresses that everyone else uses.
 
For what it's worth, my D-Link routers (DI-604/614) can perform NAT loopback quite happily wheras the Linksys one I had briefly couldn't - I don't know if it's a manufacturer-wide issue or whether it's model-specific.
 
Mathew

---

### Post by conjur3r on 2007-03-22
What MJN said.  Basically, when you access the URL from within your internal network, you are actually trying to access the modem web interface using its public IP address.  No translation is made and usually results in a page timeout due to the router denying public administration.

---

### Post by scxtt on 2007-03-22
well, the OP made it sound like "hey, i can't view my webpage using my external ip from w/in my network" - i can't speak on MJN's post, since that didn't seem to apply ...

and in terms of accessing the admin features of a router - i've never seen one that uses port 80 to do so, if i want to admin my router from outside my network, i use 8080 (if that feature is "on") - seems pretty standard to me - and i have an older router ...

---

### Post by dfreer on 2007-03-22
> well, the OP made it sound like "hey, i can't view my webpage using my external ip from w/in my network" - i can't speak on MJN's post, since that didn't seem to apply ...

Well, I can't view it using the external IP, but I didn't really expect to be able to do that. I've just been trying to access it by entering the domain name = [http://www.dfreer.org](http://www.dfreer.org). 

> The real problem comes from when you want to use name based virtual hosting - accessing by IP address will not work

This is part of my problem, thanks for noticing. From a linux machine I can modify my /etc/hosts file to point the internal IP = dfreer.org, and even specify internal IP = virtualhost.dfreer.org. Windows machines, on the other hand...  

> **[B]on a weird side note, i use homedns.org for DNS lookups for my modem IP - and i can point to it w/ any browser and get to it ... same router, same everything (well different ISP) but i'm using homedns.org ...**[/B]
Well, I assume you mean you are using DynDNS, which homedns.org is part of. I am actually using them too, with both [http://yosoko.dyndns.org](http://yosoko.dyndns.org) (the free service) and [http://www.dfreer.org](http://www.dfreer.org) (Custom DNS service). 
You say you can point to it w/ any browser and get to it ... same router? See, that is what I was thinking. I'm thinking that I simply do not have the web server set up to recognize my site, OR my ISP is causing some sort of problem. **I just wondering is there some sort of configuration I needed to do on my web server to TELL it that it is dfreer.org?**

I wanted to try using a different router, but the only other one I have is a Belkin and they do not play nice with Linux in my experience. I really don't want to have to buy a third wireless router, that would suck.

I guess I can try plugging my internet connection directly into my webserver, and then configure my web server to do DHCP and serve my LAN.

---

### Post by scxtt on 2007-03-22
i can just expand on the 2 scenarios and we'll see if you can get anything useful from them:

past scenario:

at my parents house i was running a basic apache webserver - we had my old linksys router, no wireless - and it was shared b/t my computer (2 of them, actually), my dad's and my brother's ... we had static IPs and i forwarded port 80 to my webserver's static IP ... now, as far as i can remember - in the beginning - i could type in our external IP into my browser and my webserver's pages would load (so my PC, 192.168.1.100 could browser to our external ip which forwarded port 80 to my webserver, 192.168.1.101) ... all was working happily and tho no DNS was involved (i just memorized our external ip) my dad decided to go wireless and got a new linksys wireless router ... i chose to remain wired (linux + wireless back then = headache) ... i could no longer use the external ip to connect to the webserver  as i had in the past ...

current scenario:

using the wired router i have and mentioned before - i have a similar setup as i did but w/o my brother and dad (which isn't an issue to anything above) ... i have 1 physical host and a few (+2) VMs running and at times multiple webservers (i can even set apache to listen on another port, then use that port to connect to that instance of apache - using my *.homedns.org DNS entry) ...  basically any concoction of connection methods i try allows me to connect:

*.homedns.org from w/in the LAN = works
*.homedns.org from outside the LAN = works
external ip from w/in the LAN = works
external ip from outside the LAN = works

i have port 80 pointing to an edgy server VM running zimbra and the only difference in setup that i did for that VM (following directions) is to add an MX entry for DNS and setup /etc/hosts to look like the following:
```
[font=courier]192.168.1.105   *.homedns.org       edgy-server[/font]
```

i haven't tried using my Kubuntu apache server where my hostname doesn't map to *.homedns.org in any way, so i'm not sure if that aspect matters @ all ...

maybe MJN is right for the entirety of your problem - but like i said, my wired router is OLD - so that seems strange that your router wouldn't have that "feature" - and i'm not doing anything special config-wise w/ it in terms of NAT ...

---

### Post by Mr. C. on 2007-03-22
Many routers simply do not support NAT loopback.  Nothing strange about it.

If you want to use the same name-based virtual hosts inside and outside, here are your options:

[LIST=1]
[*]For each system, add entries to your /etc/hosts file (*nix) or C:\windows\system32\drivers\etc\hosts (Windows).
[LIST]
[*]Pros: easy
[*]Cons: have to setup on all hosts, and guest's hosts when the arrive
[/LIST]

[*]Setup and run a split DNS server
[LIST]
[*]Pros: you can use your own DNS server for faster lookups; single location for hostname changes
[*]Cons: not as easy (but not difficult either)
[/LIST]
[/LIST]

MrC

---

