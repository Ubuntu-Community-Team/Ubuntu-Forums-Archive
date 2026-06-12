---
title: "LAMP server, Dynamic IP, and domain"
date: 2008-11-02
forum: Server Platforms
---

### Post by dachapa on 2008-11-02
Alright, I'm posting this question as an act desperation. I have tried following some of the examples previously posted, but I just can't seem to get my website up.

For starters, let's assume my server's IP is: 192.168.1.101 (it's dynamic)
My domain: mydomain.net (bought from iDotz.net)
And I have an account with Sitelutions

What I did with Sitelutions is that I created a host [www.mydomain.net](www.mydomain.net) to redirect to my IP (192.168.1.101). Then on iDotz control panel for my domain, the Name Servers are nsx.sitelutions.com (where X = #1-5). After this, I am able to visit my website with [www.mydomain.net](www.mydomain.net) and it takes me to the screen showing "It works!" then I try [www.mydomain.net/drupal5](www.mydomain.net/drupal5) and it shows me the Drupal login site. 

I figure that's all good and all since I have not built my site just yet BUT no one else outside my LAN can see what I see. Why is this? Help VERY MUCH appreciated.

---

### Post by MJN on 2008-11-02
Your server's IP address is what's known as a 'private' address and hence is not directly accessible over the Internet (by virtue of the Internet not routing such addresses).

Hence, in order for Internet users to access your site they need to be given the 'public' address - this will typically be the address that your ISP gives you and, specifically, is assigned to the Internet-connected WAN port of your router (which I am assuming is what you have).

Browse to something like [http://whatismyip.com](http://whatismyip.com) and it will usually be able to tell you what your 'public' address is. This is the address that you must put into the DNS configuration for your domain.

In addition to the above you will also need to set up 'port forwarding' of port 80 on your router to your server. This tells your router to send all HTTP traffic arriving at port 80 from the Internet to your server.

Having done all this you may well find you no longer have access to your website from your LAN, whereas everyone else on the Internet can. If this happens post back and we can sort that little 'gotcha' out.

Incidentally, you would probably do well to make your server address dynamic unless you can be sure your router will dish out the same address each time (many can be configured to do so by reserving it for your server's particular MAC address). Not doing this will likely mean having to reconfigure your port forwarding should the server IP ever change.

Mathew

---

### Post by jona7han on 2008-11-02
beat me to it!

---

### Post by dachapa on 2008-11-02
> **MJN said:**
> Your server's IP address is what's known as a 'private' address and hence is not directly accessible over the Internet (by virtue of the Internet not routing such addresses).

Hence, in order for Internet users to access your site they need to be given the 'public' address - this will typically be the address that your ISP gives you and, specifically, is assigned to the Internet-connected WAN port of your router (which I am assuming is what you have).

Browse to something like [http://whatismyip.com](http://whatismyip.com) and it will usually be able to tell you what your 'public' address is. This is the address that you must put into the DNS configuration for your domain.

In addition to the above you will also need to set up 'port forwarding' of port 80 on your router to your server. This tells your router to send all HTTP traffic arriving at port 80 from the Internet to your server.

Having done all this you may well find you no longer have access to your website from your LAN, whereas everyone else on the Internet can. If this happens post back and we can sort that little 'gotcha' out.

Incidentally, you would probably do well to make your server address dynamic unless you can be sure your router will dish out the same address each time (many can be configured to do so by reserving it for your server's particular MAC address). Not doing this will likely mean having to reconfigure your port forwarding should the server IP ever change.

Mathew

Ok, sounds good. After accessing whatismyip.com and typing that into my sitelutions DNS Wizard, I tried going into my website, and it took me to my Router's configuration page. Am I in the right step? I think I opened my Router's port 80, but I'm not sure if I did it right. (I'm using a Linksys Wireless-B router)

---

### Post by bep on 2008-11-02
> **dachapa said:**
> Ok, sounds good. As noob as this sounds though, when I access whatismyip.com will it give me the IP address of the computer I'm currenly using? Or do I have to visit the site from my server? If it's the latter, how does one get to browsing pages on a server? Thanks for the help.

You would have to do it from the server (well, if your server is connected to the same router, the ip is likely the same, hence the "port forwarding" needed).

Log on to server, type

wget [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp)

And look at the file created.

---

### Post by dachapa on 2008-11-02
> **bep said:**
> You would have to do it from the server (well, if your server is connected to the same router, the ip is likely the same, hence the "port forwarding" needed).

Log on to server, type

wget [http://whatismyip.com/automation/n09230945.asp](http://whatismyip.com/automation/n09230945.asp)

And look at the file created.

Right, it's the same router, so the IP is the same. I typed that IP into the DNS wizard, and my site would take me to my router's configuration page. I configured /etc/network/interfases to get up my eth1 to become static, and set the address 192.168.1.105 On my router's configuration page, I went to Applications and Gaming, and on Port Routing I typed Server, posts ranging from 79 81 to IP 192.168.1.105. I visit my site, and now it goes back to It Works. However, I believe it's still LAN-only. I don't know what to do anymore.

---

### Post by MJN on 2008-11-02
> **dachapa said:**
> However, I believe it's still LAN-only. I don't know what to do anymore.If you tell us your domain name we'll be able to help. If not, you're on your own.

Mathew

---

### Post by dachapa on 2008-11-02
My domain name is supersoccershop.net go it from iDotz.net.

---

### Post by y@w on 2008-11-02
It doesn't appear to be working. The IP I'm getting from a dig is: 24.174.250.216. Is that still your IP?

---

### Post by dachapa on 2008-11-02
Yes, that's my IP.

---

### Post by dachapa on 2008-11-03
So I managed to change route all entries through port 80 to my server, and on the DNS Configuration I set "public" IP i got from whatismyip.com. Still, however, everyone I have asked outside my LAN insist that neither [www.supersoccershop.net](www.supersoccershop.net) or [www.supersoccershop.net/drupal5](www.supersoccershop.net/drupal5) work. 

Why is it still LAN only when I already even changed the routing?

---

### Post by dachapa on 2008-11-03
.

---

### Post by CrucifiedEgo on 2008-11-03
I'm able to connect to the server on port 80, and i get a redirect to /drupal5, but i'm not getting anything on the /drupal5 site.  I think this may be why:

james@poseidon [~] $ host [www.supersoccershop.net](www.supersoccershop.net)
[www.supersoccershop.net](www.supersoccershop.net) has address 24.174.250.216

james@poseidon [~] $ host supersoccershop.net
supersoccershop.net has address 69.26.178.163

I'd suggest using a dynamic dns client (dyndns.org) and then use CNAME records to point your domain name and [www.domain.net](www.domain.net) to the dyndns hostname.  that way there's no chance of that kind of mismatch.

edit: the reason i suggest dyndns.org is because I know for sure that they work with ddclient, which is an awesome package for home servers like yours.  Make sure you reconfigure it -- the default line uses "use=eth0" which gets the local ip (192.168.x.x) -- the correct line for your config would be something like:
```
use=web, web=checkip.dyndns.org/, web-skip=&#8217;IP Address&#8217;
```

---

### Post by y@w on 2008-11-03
Looks like supersoccershop.net and [www.supersoccershop.net](www.supersoccershop.net) are pointed at two different IPs with supersoccershop.net with a redirect and [www.supersoccershop.net](www.supersoccershop.net) doesn't connect. 


Just to eliminate the obvious...

In the router you say you've configured port 80 to forward to 192.168.0.105.

From a machine on that LAN, can you telnet to port 80 on 192.168.0.105.

If the site works internally and it's pointing to the right IP from external sources, it's gotta be something simple. With Ubuntu, one thing you have to watch out for when you change from dynamic to static IPs is that you stop the dhcp client. Otherwise, it will continue to change the IP on you.

---

### Post by MJN on 2008-11-03
Have you checked with your ISP to see if they block port 80? A quick search on Road Runner suggests they do (or did).

You could try changing the port to a different number to see if this is the case.

Mathew

---

### Post by dachapa on 2008-11-03
CrucifiedEgo, that mismatch should be cleared already. I did it with sitelutions though, however I do not understand what you mean by "use=eth0".


> **y@w said:**
> Looks like supersoccershop.net and [www.supersoccershop.net](www.supersoccershop.net) are pointed at two different IPs with supersoccershop.net with a redirect and [www.supersoccershop.net](www.supersoccershop.net) doesn't connect. 


Just to eliminate the obvious...

In the router you say you've configured port 80 to forward to 192.168.0.105.

From a machine on that LAN, can you telnet to port 80 on 192.168.0.105.

If the site works internally and it's pointing to the right IP from external sources, it's gotta be something simple. With Ubuntu, one thing you have to watch out for when you change from dynamic to static IPs is that you stop the dhcp client. Otherwise, it will continue to change the IP on you.

I used telnet on my other computer to port 80, and was able to connect just fine.

MJN, I tried opening other ports or routing them to the server, such as port 82, and 81, but it seems if failed. Plus I was not able to telnet those (or that has nothing to do with this?)

---

### Post by CrucifiedEgo on 2008-11-03
The port is definitely open and working (i get the redirect mentioned earlier) so it appears that the problem is with drupal.    maybe try a static page there just to verify?  if so, then you've got it narrowed down to drupal, and you can try their support forums (or if there are any drupal experts in here, they can speak to it).

---

### Post by dachapa on 2008-11-03
I created: [http://supersoccershop.net/drupal5/?q=about](http://supersoccershop.net/drupal5/?q=about) As a static page, and my friends tell me they can't access it.

Is there a file I have to edit on my server? I seriously see myself running out of options.

---

### Post by CrucifiedEgo on 2008-11-04
The problem is, that's still a drupal page, even if it's "static"  Try creating just a basic html page that's not in drupal,and go from there.  Also, try creating a phpinfo page to make sure that php works on your server.  just put the following code in a file:
```
<?php
phpinfo();
?>
```

---

### Post by y@w on 2008-11-04
> **CrucifiedEgo said:**
> The port is definitely open and working (i get the redirect mentioned earlier) so it appears that the problem is with drupal.    maybe try a static page there just to verify?  if so, then you've got it narrowed down to drupal, and you can try their support forums (or if there are any drupal experts in here, they can speak to it).

No, the port's not listening. The old IP (the one where the redirect exists) did work. However, the destination of the redirect (24.172.250.216) is not connecting on port 80. It sounds like you are setup correctly though. I'd call your ISP and find out if they are blocking incoming connections to port 80. It appears the IP is owned by Roadrunner who has been known to block incoming connections on port 80 in the past. 


```
telnet www.supersoccershop.net 80
Trying 24.174.250.216...
telnet: connect to address 24.174.250.216: Operation timed out
telnet: Unable to connect to remote host

```

---

