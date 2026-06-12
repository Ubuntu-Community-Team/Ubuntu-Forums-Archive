---
title: "port listening on web server"
date: 2010-11-18
forum: Server Platforms
---

### Post by Phildough on 2010-11-18
So I have a basic web server, and I'm trying to get it to listen on port 8080 rather than just 80.

So I set up port forwarding on my router, configured with a dyndns address, to the server. I changed the apache2 config file to say "listen 8080". I reset apache, and it didn't work. I rebooted the server, and it didn't work... Any ideas?

So anyways, I try accessing it by typing:
blahblahblah.dyndns.blah:8080
into the url of my browser (google chrome), and it says URL was not found on this server. And then I do it again, and it must have cached or something that it can't find it, and now it says 
"Oops! This link appears to be broken."

Any help is appreciated! Thanks!

---

### Post by Ryan Dwyer on 2010-11-18
Do you realise you can let your server listen on port 80 and configure your port forwarding in your router so external 8080 goes to internal 80?

Also, DynDNS and similar services will use your external IP address. If you're in the same local network as your server then you need to use its private IP. DynDNS is only for accessing stuff from over the internet - don't use DynDNS for accessing it locally.

---

### Post by trentscott on 2010-11-18
> **Ryan Dwyer said:**
> Do you realise you can let your server listen on port 80 and configure your port forwarding in your router so external 8080 goes to internal 80?

Also, DynDNS and similar services will use your external IP address. If you're in the same local network as your server then you need to use its private IP. DynDNS is only for accessing stuff from over the internet - don't use DynDNS for accessing it locally.

+1 I would configure port 8080 to forward to port 80 on your server's LAN IP. You can run the command ifconfig to figure that out.

---

### Post by Phildough on 2010-11-18
> **Ryan Dwyer said:**
> Do you realise you can let your server listen on port 80 and configure your port forwarding in your router so external 8080 goes to internal 80?

Lol, actually, I had no idea. That's awesome!
I have a linksys WRT52G (just a standard, run of the mill linksys...).
So just to make sure I got this right, I would go to the "Applications & Gaming" tab tell BOTH port 80 AND port 8080 to be forwarded to the local static IP of my server, and then under "Port Triggering" I would put the "triggered range" to 8080 and the "forward range" to 80. 

Is that correct?

> **Ryan Dwyer said:**
> 
Also, DynDNS and similar services will use your external IP address. If you're in the same local network as your server then you need to use its private IP. DynDNS is only for accessing stuff from over the internet - don't use DynDNS for accessing it locally.
Yes, but I'm running in to problems accessing it over the internet. I previously posted a thread about this problem, and it remains unsolved, but I could access it locally both through the dyndns name and the local IP, but it would not let me access it through the dyndns name when I was anywhere but my apartment. We did, however, figure out that, since the router is configured with the dyndns thing anyways, it knows to just immediately forward it to the local IP if you are trying to access it with that name from anywhere locally. 
The problem with accessing it globally is why I want to try to change which port it's on to see if that helps anything.

---

