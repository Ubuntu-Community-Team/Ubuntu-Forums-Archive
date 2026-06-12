---
title: "http://myserver works, but I want to make it http://myserver.local"
date: 2010-12-04
forum: Server Platforms
---

### Post by statikeffeck on 2010-12-04
I'm not sure what system or package needs to be configured to do this. Is it Apache or DNS, or something else? 

Basically I have a run of the mill Ubuntu LAMP server on my LAN, and I can get to it out of the box from another computer by going to **[http://myserver](http://myserver)** -- "myserver" is the hostname I chose during server installation.

But thats kind of weird, I'd rather configure it so it looks like a domain name (FQDN) -- such as **myserver.com** or **myserver.net**. This is all for my internal network only, I don't need to access the web server externally.

Edit: so when Computer 1 makes a request for [http://myserver.net](http://myserver.net), I want Computer 2 to respond to it. I suppose I could modify the HOSTS file on Computer 1 to automatically map the domain name to an IP address.  but then I have to configure that HOST file on additional computers, and for each domain name.

Edit2 (SOLVED): Unless you use the HOSTS file method on each client machine to map the IP address, this just isn't possible without going to a full blown DNS method.

---

### Post by Coder68 on 2010-12-04
You will need to use the HOST file or install DNS and add a record for it.

I don't know of any other way.

Coder68

---

