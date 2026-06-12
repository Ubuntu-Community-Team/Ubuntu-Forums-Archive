---
title: "Looking to install a simple proxy server"
date: 2009-07-21
forum: Server Platforms
---

### Post by indispus on 2009-07-21
Hello!

I am currently running a proxy server under Vista, named "CCProxy".
In my basement I am running a Ubuntu machine (WEB, Database, Torrent, FTP), and I was thinking that I can use that machine to run the proxy server.

At work, all ports except the usual ones, are closed. I am using my current home proxy server in order to access the closed ports from work.


My question is: what proxy server do you recommend to use for my needs? I am looking for something very simple and light, and something that will not affect my current servers (everything is working great so far). I don't need caching, or things like that.

Is Squid OK for my needs? Can I use it without to affect my current servers, and without caching anything?

Cheers!

---

### Post by NewbieNik on 2009-07-21
I am using Squid and have turned caching to 512Kb, I believe you might be able to set it to 0Kb, but would need to test it to confirm after all Squid IS a proxy-cache.
If you do not set your existing servers to use this as a proxy then, no it shouldn't affect them, but you can turn on the Invisible proxy which will catch ALL traffic.
It's not overly light-weight though. If anyone has any better suggestions, feel free to chip in.....

---

