---
title: "Web Server Access"
date: 2010-11-19
forum: Server Platforms
---

### Post by Phildough on 2010-11-19
I have a web server set up using apache, and an assigned dyndns address. I have port forwarded both 80 and 8080 to the static IP of of the server, on my router. I have port 8080 set to trigger to port 80. The apache config file is set to listen on both of these ports. I have the "index.html" file in the default /var/www/ folder, and permissions for both of these folders allow for reading by anybody.

I can access the website through a browser from my apartment by typing either the server's local IP address or the dyndns assigned domain name that is configured with my router. It does not work from my apartment when I append ":8080" to the either URL.
From anywhere BUT my apartment, I cannot access the website, regardless of what method I use.

However, I can access the server via ssh/sftp, and ftp from anywhere, using the dyndns assigned domain name. 

Why can I not access the website from anywhere except for my apartment? I have asked this on this forum before, and I have tried everything anyone has suggested, and it remains unsolved. I know it must be a stupid mistake on my part, so any suggestions, no matter how obvious, would be helpful!

PLEASE help me get this working! I've been trying for so long and really want it up! :(

 Thanks! :)

---

### Post by wongo888 on 2010-11-19
From **outside** your network, try (with your IP):

```
$  nmap -p 80,8080 -A 123.123.123.123
```

You can also try using a web service like:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

...to test port 80.

ISPs sometimes filter port 80 traffic, so check with their support system (sometimes a forum).

Make sure that you have not enabled remote router administration on port 80, otherwise your router's admin interface will be serving on port 80 rather than proxying your port 80 requests into your LAN.

---

### Post by Phildough on 2010-11-19
> **wongo888 said:**
> 
You can also try using a web service like:
[http://www.canyouseeme.org/](http://www.canyouseeme.org/)
...to test port 80.


OK I tested port 80, and it timed out. But then I tested 8080 and it said it could see me. Say I give up on trying to use 80, and force using 8080 to access the website. What am I doing wrong that prevents that from working?

I have 8080 port forwarded on the router, and I have the server listening on 8080 as well. Someone suggested last time that you can have the router filter incoming port 8080 requests and translate it to an 80 request to the server (so the server only has to listen on 80) and I did that through port triggering. (That's what port triggering is... right?). I have the server listening on both, the router forwarding on both, AND the port triggering from 8080 to 80. Yet 8080 doesn't work from ANYWHERE, and 80 works only in my apartment. Oddly enough, canyouseeme only sees 8080, and not 80...

---

### Post by wongo888 on 2010-11-19
I think that you're making this more complicated than it needs to be. I'd turn off the port triggering feature - I've never had to use it - ever. I have several machines serving stuff from behind my Linksys router.

All you need to do is ensure that any inbound traffic from the Internet hitting your router on port 80 gets forwarded to your web server within your LAN on port 80. This should be a simple configuration.

[http://portforward.com/](http://portforward.com/)

If your external port 80 (on your firewall/router) still not working after following those instructions then you might have to follow-up with your ISP and ask them if they are blocking port 80 traffic for some reason.

---

