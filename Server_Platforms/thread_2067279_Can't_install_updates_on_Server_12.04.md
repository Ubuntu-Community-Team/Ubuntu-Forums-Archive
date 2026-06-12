---
title: "Can't install updates on Server 12.04"
date: 2012-10-06
forum: Server Platforms
---

### Post by pstonge on 2012-10-06
Hey guys, I was wondering if anyone can help me out with this.
 
I just installed 12.04 server on VirtualBox, i have everything set up properly. 
Bridged connection to my Host PC. This ubuntu server is going to be a proxy server for our company. I have the DNS records (A) & (PTR) set for the name of the server. I checked ifconfig and I am in the proper network. I entered in the proxy settings that we currently use, [http://192.168.12.5]("http://192.168.12.5/"), into my server.
I have been reading post, and they say to add my username&password then my IP for proxy but, that should not work because my server is not on the domain yet. And when I take the proxy off, I can't get anything. 
 
But here is some example text from the out put of apt-get update;
(it is an attachment, can figure out how to past an image here)
 
 
I have tried a bunch of things, but still new to ubuntu, let alone server edition.

---

### Post by craigp84 on 2012-10-06
It looks like you've not specified any authentication credentials and your proxy upstream is configured to require these before permitting your request to be serviced.

The two simplest options would be 1) supply valid authentication details to apt for the upstream proxy or 2) disable authentication from your new host's IP.

Hope this helps

---

