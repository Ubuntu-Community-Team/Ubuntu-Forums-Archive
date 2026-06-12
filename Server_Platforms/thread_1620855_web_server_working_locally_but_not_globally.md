---
title: "web server working locally but not globally"
date: 2010-11-13
forum: Server Platforms
---

### Post by Phildough on 2010-11-13
I cannot connect to my server's website from anywhere except my local network. I've set up a dyndns account, and forwarded all necessary ports on my router, and don't know what to do. It works by putting the dyndns address in the web bar (which is linked to the real IP address of the router, not the local IP address) when I'm local, but anywhere else, it doesn't. This doesn't make sense to me, because if I'm using the dyndns address, it still has to find it's IP address through my internet provider, so it should be the same as accessing it anywhere globally... right? 

Also, ssh, ftp, and sftp all work fine BOTH locally and globally... using the dyndns address for them too. 

Any ideas how I can get the website up for anywhere other than my apartment?

---

### Post by lisati on 2010-11-13
Assuming that port forwarding in your router is working correctly, it is possible that your ISP is blocking port 80.

---

### Post by Phildough on 2010-11-13
> **lisati said:**
> Assuming that port forwarding in your router is working correctly, it is possible that your ISP is blocking port 80.

If that were the case, would it not also not work locally when I use the dyndns-given address? I mean, when I type that address in a browser, no matter where I am, it should go to my ISP, check to see if it can translate it to an IP address, if it can't go deeper to a DNS, etc... until it can, in which case it will return to my router and access it from outside. IE- no matter where I am, if I am accessing it via its domain name, it SHOULD be accessing it from outside my router... right?

---

### Post by lisati on 2010-11-13
> **Phildough said:**
> If that were the case, would it not also not work locally when I use the dyndns-given address? 

Good call. That makes sense. I think I better get myself another cup of coffee while I ponder other possibilities. :)

---

### Post by Strategist01 on 2010-11-13
I've found that with my router you might have to specify port 80. I know you shouldn't have to, but sometimes that's all that is needed. I also have a dyndns account.

---

### Post by Phildough on 2010-11-13
> **Strategist01 said:**
> I've found that with my router you might have to specify port 80. I know you shouldn't have to, but sometimes that's all that is needed. I also have a dyndns account.

I have already :/

Also, why shouldn't you have to? I think you DEFINITELY should have to, otherwise how would it know what local IP address to go to? (otherwise, someone searching your website could end up on some guy's machine who happens to be on the same network)

---

### Post by Strategist01 on 2010-11-14
> **Phildough said:**
> I have already :/

Also, why shouldn't you have to? I think you DEFINITELY should have to, otherwise how would it know what local IP address to go to? (otherwise, someone searching your website could end up on some guy's machine who happens to be on the same network)

You shouldn't have to because all web browsers automatically point all connections through port 80 on http.

However, make sure you have your ports forwarded correctly - and the guy on your website wold have to connect to another port on your website. I.e., if you forward port 80 in your router so that if I type in your dyndns account it directs me to your webserver; I can't access other machines on port 80. You would have to set up another port to forward to another machine.

BTW, if your ISP does block port 80, you may have to open it on another port, above port number 1100. Unless you tell people which port to go to, i.e they type dyndns.org: port you might have to get a redirection service to make it point to the port you specified if they just type in your dyndns address.

Cheers!

---

### Post by Phildough on 2010-11-14
> **Strategist01 said:**
> 
BTW, if your ISP does block port 80, you may have to open it on another port, above port number 1100. 


Alright- I'll give that a try. I thought we ruled out the ISP blocking port 80 through the reasoning a couple posts above...  Oh well, can't hurt to try :P

---

### Post by Phildough on 2010-11-14
K that didn't work :(.

I'm not trying to spam, so this is the last time I'm bumping this thread, cuz I figure it's better to bump an unsolved thread than create a new identical one... I'd just really like to get this fixed :(

But yeah, if it doesn't get fixed this time, I'll leave it alone to die

Thanks!

---

### Post by gmargo on 2010-11-14
Are you absolutely sure that you are forwarding port 80 from the router to your internal machine?  If you have ssh working then port 80 should work.  I doubt the ISP is blocking it.  Also, do you have a firewall running that might be blocking things?

I would try using telnet from the outside to verify connectivity ("telnet yourhost.dydns.com 80"), and compare that to port 22 (if that's the port you're using for ssh).

(Personally I use a non-port-22 and a non-port-80 just to cut down on the script kiddy attacks.)

> 
Also, ssh, ftp, and sftp all work fine BOTH locally and globally... using the dyndns address for them too. 
The router is probably configured to route back to you if you specify the external dydns address.  So it is conceivable that it works internally (due to route-back) but not externally (due to non-forwarding??)

---

### Post by James78 on 2010-11-14
Probably not related to your problem, but I have an option in my router "Block Anonymous WAN Requests (ping)", and this stops anyone else from being able to reach me from WAN. I myself can get here even if I use the external IP, this is because of a loopback. So disabling this option for me allowed everyone else to see and use the server.

---

### Post by arvevans on 2010-11-14
If you have a Cable or DSL modem, it may have a firewall that is blocking things.  

If you have a local WiFi-Hub-Router you will need to open a hole in that unit's firewall and specify that incoming initial packets for port-80 go specifically to the server itself.  My guess is that this may be your problem.  You can do your own connect via DynDNS because you are initiating it as an outbound session, which will then allow the inbound session to complete.

I too use DynDNS, DSL, and a Netgear WiFi-Hub-Router to support my in-house LAN.  Proof that it works is located [*_here_*]("http://qrp.webhop.net/").

---

### Post by Phildough on 2010-11-17
That seems to be the problem, I had no idea the router knew to translate the dyndns thing before sending it off... cool haha

So anyways, yes, port 80 was most definitely set up for port forwarding. I have yet to have the chance to test it from outside, but I figure I'll change the port anyways (script kiddy blocking = probably a good idea). 

So I set up port forwarding on 8080, and changed the apache config file to listen on 8080.

NOW when I try to access it (via: [http://blah.dyndns.blah:8080](http://blah.dyndns.blah:8080)) it says "oops, link is broken!". When I try a random unassigned port it says "Cannot access this". So it's registering SOMETHING different with the port 8080... but I don't know what.

Any ideas?

*edit* Wow, didn't even see that there was a second page- up until here this post was replying to the last post on the first page...

Anyways- how can I create a hole in the firewall? I assumed the router was what had the firewall, and port forwarding in itself was the equivalent of creating a hole...

Thanks!

---

### Post by Strategist01 on 2010-11-20
> **Phildough said:**
> That seems to be the problem, I had no idea the router knew to translate the dyndns thing before sending it off... cool haha

So anyways, yes, port 80 was most definitely set up for port forwarding. I have yet to have the chance to test it from outside, but I figure I'll change the port anyways (script kiddy blocking = probably a good idea). 

So I set up port forwarding on 8080, and changed the apache config file to listen on 8080.

NOW when I try to access it (via: [http://blah.dyndns.blah:8080](http://blah.dyndns.blah:8080)) it says "oops, link is broken!". When I try a random unassigned port it says "Cannot access this". So it's registering SOMETHING different with the port 8080... but I don't know what.

Any ideas?

*edit* Wow, didn't even see that there was a second page- up until here this post was replying to the last post on the first page...

Anyways- how can I create a hole in the firewall? I assumed the router was what had the firewall, and port forwarding in itself was the equivalent of creating a hole...

Thanks!

Hi there, port 8080 is a port used for internal LAN proxies (ones that give internet access to all the PCs in a LAN) so I think that your PC may be confusing ports, could be reserved. Try something like 8081?

To make a hole in your firewall, you would have to go to Packet filtering or Port Filtering. Not too sure what firewall your router has, but in those rules I think you would have to set up something similar to this: > ([IMG]http://admin:fljgfqqq@10.0.0.2/images/Note.gif[/IMG]*If  some applications cannot work after enabling Firewall, please check the  Packet Filter especially Port Filter rules. For example, adding  (TCP:443,outbound allowed) will let HTTPS data go through Firewall.)*

That's what my router's firewall says to do to open ports. You would have to open it for inbound and outbound, and TCP and UDP possibly.

---

### Post by slim902 on 2012-02-20
> **James78 said:**
> Probably not related to your problem, but I have an option in my router "Block Anonymous WAN Requests (ping)", and this stops anyone else from being able to reach me from WAN. I myself can get here even if I use the external IP, this is because of a loopback. So disabling this option for me allowed everyone else to see and use the server.

 Thanks!! This allows my server to work outside my home network. I tried every thing all weekend and all i had to do was uncheck a box in my router settings!  I even tried reinstalling ubuntu haha noob

---

