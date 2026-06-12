---
title: "How to host a webpage on your own server."
date: 2009-07-15
forum: Server Platforms
---

### Post by irv on 2009-07-15
I remember back when I was thinking about hosting my own website on my own server but didn't know how to go about doing this. So I did a search on the web looking for all the answers so I could get it setup right. Because of this and seeing newbies on this board asking question about trying this same thing I thought I would put together this short "howto" to maybe answer some of the questions they might be asking. 

If any one wants to add to this feel free to do so. 

With that said here is how I got my website to be hosted on my own server.

First, I got a static ip address from my service provider, then I got a domain name and had the domain name bound to that ip address. Here is the screenshot to how I bound it on the Domain Name Server (DNS). (When you first do this it might take up to 24 hour to be bound.)
[ATTACH]121158[/ATTACH]
Next I setup my router that allow me to host that ip address. This allow anyone who types my URL in a browser which point my URL to that ip address on the DNS and in turn finds my ip address on my router. Again here is a screenshot.
[ATTACH]121159[/ATTACH]
Next, I had to give my server a static ip address on my network so I could open all the ports in the router for http, ftp, etc. Again here is a screenshot:
[ATTACH]121160[/ATTACH]
The only thing left now was to setup the server which I am not covering in this "howto". But after you do this you should be able to host your own website.

---

