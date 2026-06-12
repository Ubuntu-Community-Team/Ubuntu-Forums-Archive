---
title: "Detecting a compromised script on my server"
date: 2008-12-27
forum: Server Platforms
---

### Post by huanix on 2008-12-27
I returned from holiday break and did a little traffic sniffing on my server and noticed what appeared to be outgoing traffic from my Ubuntu 8.04 http (LAMP) server to victim sites. (See attachment for what I got.)

My server is for personal websites, so I immediately shut it down. 

I fired it back up this morning to investigate. I believe a script on my server is calling sites to set up spam accounts, but not all of them- one of note was [http://ebmex.t35.com/CheckProxy.php](http://ebmex.t35.com/CheckProxy.php) (now blocked)

I disabled the site that appeared related to the call (a moodle for my wife's classroom), but I can't figure out what is generating the request. 

There isn't much in the logfile for the site, 99.9% is a cron maintenance script, which doesn't appear to be compromised. 

Even after disabling that site, and ALL cron jobs, I am still seeing this outgoing traffic.

I recently had a hard time getting mod_proxy to work, so it's a permissive install - this could be the culprit, but i wanted to check to see if anyone else has ideas or a clear explanation of what's going on.

---

### Post by huanix on 2008-12-27
As the pieces fall together in my head, it appears that someone used my permissive setup of mod_proxy as a jumping off point to harass other sites. I disabled proxy_http and proxy until I can get a secure setup... does this sound correct to anyone else?

---

### Post by albinootje on 2008-12-27
> **huanix said:**
> As the pieces fall together in my head, it appears that someone used my permissive setup of mod_proxy as a jumping off point to harass other sites. I disabled proxy_http and proxy until I can get a secure setup... does this sound correct to anyone else?

I don't know about that, but do you have any links to email-archives on your website ?
I read that certain links to search-engine links can be abused by visitors.

And what about php-scripts and cgi-scripts ?
Securing/hardening php and cgi is something you should read about.

---

### Post by hictio on 2008-12-27
> **albinootje said:**
> I don't know about that, but do you have any links to email-archives on your website ?
I read that certain links to search-engine links can be abused by visitors.

And what about php-scripts and cgi-scripts ?
Securing/hardening php and cgi is something you should read about.

++
Also, have you scanned your system with a Root Kit Hunter, like, [Root Kit Hunter](http://www.rootkit.nl/projects/rootkit_hunter.html)?

---

### Post by huanix on 2008-12-27
I've been monitoring outgoing traffic all day, and it seemed to completely stop when i disabled proxy and http_proxy.

---

### Post by albinootje on 2008-12-27
> **huanix said:**
> I've been monitoring outgoing traffic all day, and it seemed to completely stop when i disabled proxy and http_proxy.

Proxy and http_proxy are by default not enabled in apache2 on Debian, and also not in Ubuntu i assume.

Do you need those apache modules again ?
Lighttpd is an interesting and security-focused apache alternative, which also can do proxy-ing, there's less to configure in the lighttpd config file, but the syntax is different, and also cgi is handled differently.

I was curious to know more about this, and found this :
[http://wiki.apache.org/httpd/ProxyAbuse](http://wiki.apache.org/httpd/ProxyAbuse)
Is that useful for you ?

And see Post #8 here :

[http://74.125.77.132/search?q=cache:noOra7CEaLwJ:forum.spamcop.net/forums/index.php%3Fshowtopic%3D7165+apache+proxy+botnet+abuse&hl=en&ct=clnk&cd=6&gl=uk](http://74.125.77.132/search?q=cache:noOra7CEaLwJ:forum.spamcop.net/forums/index.php%3Fshowtopic%3D7165+apache+proxy+botnet+abuse&hl=en&ct=clnk&cd=6&gl=uk)

---

### Post by huanix on 2008-12-27
Thanks albinootje. I was in a rush to get a zoneminder install set up before i went on vacation, and i used mod proxy to forward requests from my primary server to my zoneminder box. (By the way, ZoneMinder is absolutely awesome!). I enabled mod_proxy but had difficulty getting the conf right before I left. The next time I set it up I can be sure I enable it in a secure way. 

I have used lighthttpd here and there (on my iphone and wii), but I have been a fan of Apache for several years and don't see changing that any time soon, but I do appreciate the suggestion.

The links regarding proxy abuse explained my issues very clearly. I'm still going to run a rootkit check, but that's just precautionary - i think I'm resolved.

Thanks again.

---

### Post by albinootje on 2008-12-27
> **huanix said:**
> Thanks albinootje. I was in a rush to get a zoneminder install set up before i went on vacation, and i used mod proxy to forward requests from my primary server to my zoneminder box. (By the way, ZoneMinder is absolutely awesome!). I enabled mod_proxy but had difficulty getting the conf right before I left. The next time I set it up I can be sure I enable it in a secure way. 

I have used lighthttpd here and there (on my iphone and wii), but I have been a fan of Apache for several years and don't see changing that any time soon, but I do appreciate the suggestion.

The links regarding proxy abuse explained my issues very clearly. I'm still going to run a rootkit check, but that's just precautionary - i think I'm resolved. 

Okay, cool! :)

---

