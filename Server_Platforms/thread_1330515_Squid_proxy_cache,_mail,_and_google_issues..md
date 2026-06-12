---
title: "Squid proxy cache, mail, and google issues."
date: 2009-11-18
forum: Server Platforms
---

### Post by munchi3s on 2009-11-18
I am system administrator for a lab at my high school. I am doing all of my servers via ubuntu server 9.10. I have squid3 setup as a transparent proxy and it works for all things internet except any mail connections via client or browser and google apps wont work as well. I would like to keep my squid server in place to prove it worth instead of setting up a nasty ISA server.

Any and all help appreciated very much

---

### Post by Bag-O-Stuff on 2009-11-18
What about other pages that use https?  Do they work?  I'll bet they don't.  An alternate solution with the tools you have would be to not use the transparent proxy and set it up as a normal proxy and then force the browsers to use the proxy.  This can be pretty easy to do in both IE and Firefox.  I use squid as https proxy all the time in this manner.

[http://www.faqs.org/docs/Linux-mini/TransparentProxy.html](http://www.faqs.org/docs/Linux-mini/TransparentProxy.html)

---

### Post by kewlrichie on 2009-11-18
I spent hours trying to figure out why https sites didnt work after searching around and checking other guides I came across somewhere that said I would need to enable ip_forward so this should fix it ```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` this should allow traffic from other ports like httts/ssl 443 be forwarded through

---

### Post by munchi3s on 2009-11-19
> **kewlrichie said:**
> I spent hours trying to figure out why https sites didnt work after searching around and checking other guides I came across somewhere that said I would need to enable ip_forward so this should fix it ```
echo 1 > /proc/sys/net/ipv4/ip_forward
``` this should allow traffic from other ports like httts/ssl 443 be forwarded through

My transparent proxy works great and as for https sites they work great also
It was only mail that was giving me the problem. I use a script for my iptables that I edit accoridngly and I figured out what the problem was. at the end of my iptables script its 

iptables -A INPUT -j DROP

and that tells the system to drop everything that it doesnt ask for then I add accpeted ports above this line.
The only problem was that the ports for mail was blocked. Not an issue with https.
Now I still have a problem. My squid proxy server is super great except it won't cache Microsoft's windows live product and so all 30 students have to download it at the same time which destroys the network.
But other than that my transparent proxy server is perhaps my greatest accomplishment when it comes to the school's tech lab.

---

### Post by Drezard on 2009-11-19
What windows live products? and what do you mean by download them each time?

---

### Post by munchi3s on 2009-11-20
> **Drezard said:**
> What windows live products? and what do you mean by download them each time?

I am system administrator of a our school tech lab. I set up a squid proxy-cache server so we can monitor and cache information on the server so that when the lab is filled with 30 or so kids in the lower technology courses everyone can use the internet effectivly. Right now in IT-02(Second Year Tech Class) Our teacher is doing a 3 week lesson on windows and is using Microsoft's Windows Live essentials which is live mail, live writer, etc... And it takes 40 minutes to download the whole product at max speed. Thats just one student downloading it if you have 30 students all downloading it at the same time it could take a day or two. So I am trying to figure out why my squid proxy server wont cache it...

---

### Post by Bag-O-Stuff on 2009-11-20
I don't think squid actually caches SSL traffic though.  It just relays the requests to the other end.  Squid would have no idea what the content is because it's encrypted.

[http://wiki.squid-cache.org/SquidFaq/AboutSquid#Does_Squid_support_SSL.2BAC8-HTTPS.2BAC8-TLS.3F](http://wiki.squid-cache.org/SquidFaq/AboutSquid#Does_Squid_support_SSL.2BAC8-HTTPS.2BAC8-TLS.3F)

Could you download the product once and have it saved somewhere locally and install from there?  Most products have some sort of network install for the sys admins.  Acrobat Reader, for example.  They want you to download the small program that then goes and gets the whole program from the internet.  But you can simply download the entire thing as an alternative and install on multiple computers.

---

### Post by koenn on 2009-11-20
> **munchi3s said:**
> I am system administrator of a our school tech lab. I set up a squid proxy-cache server

... And it takes 40 minutes to download the whole product at max speed. Thats just one student downloading it if you have 30 students all downloading it at the same time it could take a day or two. So I am trying to figure out why my squid proxy server wont cache it...

That's probably because of the size of the files. Proxies have a maximum file size that they will cache. It's configurable in squid, actually.


But the correct approach here would be to download the program(s) yourself, and make them available from a server on the lan (web, file share, ...) or, better yet,  through a software distribution system. I don't know many sysadmins who expect the users to just download stuff from the internet and install it - all sorts of nasty things can happen.

---

