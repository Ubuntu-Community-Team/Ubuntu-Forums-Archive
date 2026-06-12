---
title: "server and domain problem"
date: 2006-11-28
forum: Server Platforms
---

### Post by notcrunk on 2006-11-28
OK I have two problems.

1. I finally got my server up, I hope.  But I can't test it.  Since all of my computers are hooked up to the same modem with a router I don't trust them.
The address should be [http://192.168.1.102](http://192.168.1.102)

2. I want to use a free domain name from [http://www.dot.tk](http://www.dot.tk) but they say the url doesn't exist or is already a redirected url.

---

### Post by Compact on 2006-11-28
[192.168.1.102]("http://192.168.1.102/") this ip is a private ip, so anyone will be able to use it from the internet. 
To check if the server is accessible trought internet, you can check the http headers with this website: [www.nwtools.com](www.nwtools.com)

---

### Post by MJN on 2006-11-28
Just to rephrase what Compact has correctly said, 192.168.1.102 is a so-called private address ([http://www.rfc-editor.org/rfc/rfc1918.txt](http://www.rfc-editor.org/rfc/rfc1918.txt)) and hence is only valid within your LAN and not routable on the Internet.
 
However, your ISP will have assigned you a public IP address - find this out by going to [whatismyip.com]("http://www.whatismyip.com") and making a note if it.
 
The public address is what you'd need to point your .tk domain to (although if your IP changes you'd need to update the DNS for your domain - but that's for another discussion).
 
For your .tk domain I'm unclear as to what the error was - can you post again with it copied-and-pasted? It could either be that the name is already taken, or that you've attempted to use your private IP address instead of your public one and it's detected it. Although I would expect it to have given a more specific error message if this was the case.
 
Mathew

---

