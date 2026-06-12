---
title: "Server using DMZ or internal with Port Forwarding?"
date: 2010-04-20
forum: Server Platforms
---

### Post by JavaBeanHead on 2010-04-20
Hi gurus . . .
 
New server install soon here . . . it will be primarily a web server, but will also be a mail server, I think. Not real sure how that works yet.
 
Anyway: Do you recommend I configure it (using my router) to be 'external' on the router's DMZ? Or should I instead leave it on my class C (192.168.x.x) network and poke holes in the router firewall to enable it to serve pages to the Internet?
 
Risks/benefits of each?
 
Thanks,
JavaBeanHead

---

### Post by ICEB3AR on 2010-04-20
I would say if your router has the feature of DMZ you should use this, because it is exactly that what you need.

If you put in your Server into your "Normal" Network there is a bit more configuration i think. So e.g. Portforwarding to the server and there is much more work on making the network save.

---

### Post by JavaBeanHead on 2010-04-20
Okay, great - this is good information. So, my ISP's servers will give my server an address (which would be equivalent to my external address) via DHCP, then, right? Hence I wouldn't want to configure a static IP when I'm configuring the server. Correct?
 
Also - will having a server on the DMZ still allow me to host more than one website (i.e. via virtual hosting)?

---

### Post by BobVila on 2010-04-20
> **ICEB3AR said:**
> I would say if your router has the feature of DMZ you should use this, because it is exactly that what you need.

If you put in your Server into your "Normal" Network there is a bit more configuration i think. So e.g. Portforwarding to the server and there is much more work on making the network save.

I couldn't disagree more. Internal with ports forwarded is a much safer option. Putting a server in the DMZ, outside of rare cases, screams "lazy admin." 

Think of it this way - do you want ~10 attack vectors available for port scanners/hackers, or several thousand?

---

### Post by ICEB3AR on 2010-04-20
Isn't it nearly the same if the Port is open on the router or on the Server? When The Server is right configured with all necessary rules in the FW it is - to my mind - safer in the DMZ, because if your server gets hacked it can not make that damage it could if it is not there. That is the concept of a DMZ. Although why should it be different to a port scan on the router or on the server. It everything is a question of configuration.

Just my mind.

---

### Post by JavaBeanHead on 2010-04-20
That's what forums are all about! Opinions and discussion! 
 
So . . . is there a guide on what to look out for when setting up a server internally? How do I keep it [hackers] isolated from my other personal stuff (freenas, desktop, laptops, etc.)?

---

### Post by Vegan on 2010-04-20
I use the Linksys as a firewall and only let port 80 through for now, more coming down the road.

---

### Post by JavaBeanHead on 2010-04-21
If I install mailserver functionality on the same box, is there any hazard of hosting the device externally (DMZ)? 
 
Any other thoughts on internal/portforwarding versus external/DMZ?

---

### Post by tgalati4 on 2010-04-21
Only use DMZ if you want to study attacks and collect information on what sites are trying to get in.  You might be both surprised and frightened.  Just check your log files after leaving your machine in the DMZ for a few weeks.

Better to put it in a normal router slot and port-forward those ports required by your services.

---

### Post by koenn on 2010-04-21
> **BobVila said:**
> I couldn't disagree more. Internal with ports forwarded is a much safer option. Putting a server in the DMZ, outside of rare cases, screams "lazy admin." 

Think of it this way - do you want ~10 attack vectors available for port scanners/hackers, or several thousand?

Public servers belong in a DMZ - that's how it's done. Ports forwarding into the LAN screams "amateur".

Like ICEB3Ar says. the purpose of DMZ is to 
a/ avoid untrusted connections into your LAN
b/ contain the damage in case a publicly accessible server gets compromised : If a server on your LAN gets compromized, the attacker is instantly on the LAN side of your perimeter firewall, on a trusted host, possibly with easy access to other hosts on the LAN. You don't want that. 


Obviously, you'd still need a firewall between the internet and your DMZ (or on the server(s) in the DMZ), you're not going to just leave them standing there. And you don't run services you don't need, and set things up securely, etc, etc, etc. 

One thing to check is what exactly the router manufacturer means by "DMZ" - on home appliances they tend to use it for miscellaneous configurations that are not always real DMZ.

---

### Post by koenn on 2010-04-21
> **JavaBeanHead said:**
>  
So . . . is there a guide on what to look out for when setting up a server internally? How do I keep it [hackers] isolated from my other personal stuff (freenas, desktop, laptops, etc.)?
you set up a firewall on all of your other stuff (nas, desktop, laptops, etc) so that they block connections/traffic coming from that server. 


Alternatively, you set up a firewall *between* the server on one hand, the nas, desktops, ... on the other hand. Essentially, that's putting the server in a DMZ.

---

### Post by bab1 on 2010-04-21
Edit: Grabbed the wrong quote earlier -- correct now.

> **BobVila said:**
> I couldn't disagree more. Internal with ports forwarded is a much safer option. Putting a server in the DMZ, outside of rare cases, screams "lazy admin." 

Think of it this way - do you want ~10 attack vectors available for port scanners/hackers, or several thousand?

What?  A proper DMZ has the firewall/router either as two devices with the DMZ between them and the rest of the network behind the second router (router--dmz--router--internal) or a single router with 3 interfaces.

No need to have all the servers with firewalls on each host.  You only need to stop attacks once; at the edge

See [**_here_**]("http://www.google.com/images?q=network+dmz&um=1&ie=UTF-8&source=univ&ei=KW7PS-_-GpHgtgPNsaHeBg&sa=X&oi=image_result_group&ct=title&resnum=4&ved=0CCUQsAQwAw").

---

