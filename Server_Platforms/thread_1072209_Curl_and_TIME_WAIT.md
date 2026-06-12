---
title: "Curl and TIME_WAIT"
date: 2009-02-17
forum: Server Platforms
---

### Post by mrdek11 on 2009-02-17
Hi There!
I work daily with many scripts that interface with web applications using cURL. (The ones I'm working with specifcially now interface with a PHP based online game, and therefore use cookies and sessions.)

Recently I discovered that cURL is opening hundreds of TIME_WAIT connections, that remain open for quite a while after the scripts are completed. These connections are effectively DDOSing my own server, causing the network ports to slow down.

I've looked everywhere for some solution, and have only found false leads. I even went so far as to enable tcp_tw_recycle and tcp_tw_reuse temporarily, and they, as well, had no effect. 
[EDIT] I actually just realized that I must not have truly enabled them. (which is probably a good thing, as I've since learned they are very dangerous). All I did was edit the 0s in the respective files in /proc/sys/net/ipv4/ to 1s.[/EDIT]
I have tried calling curl with a header parameter (-H "Connection: close") to prevent a Keep-alive connection. I've tried using a --connect-timeout 10 attribute, hoping it would kill the connections after 10 seconds, but they still remain in TIME_WAIT for up to five minutes after the scripts are complete.

Has anybody else encountered this, or does anybody know what I should do?
I appreciate your time and effort in assisting me!

  Derek

---

### Post by mrdek11 on 2009-02-18
Alright, I found out how to edit those system variables permanently (using sysctl), but they still don't help.
Any ideas?

---

