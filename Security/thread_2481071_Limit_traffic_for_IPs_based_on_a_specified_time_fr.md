---
title: "Limit traffic for IPs based on a specified time frame"
date: 2022-11-18
forum: Security
---

### Post by Elmi77 on 2022-11-18
Hi,

I have an webserver running which provides an archive of binaries which is quite big. Now from time to time a bad web robot passes by pulling ALL these binaries completely without any speed limit causing a traffic of several dozen GBytes within a few minutes. The bot itself can't be identified as it does not come with a specific client identification, it looks like just a stupid browser without any additional information.

So my only idea to defend from this bot, is to limit the traffic. Means I'm looking for a solution to define a maximum traffic a single IP is allowed to pull from my server within a given time frame.

Any idea how this can be done? Is there a possibility in Apache to define such traffic limits? Or perhaps somewhere within fail2ban?

When searching the web for this problem, I only stumble upon solutions that limit the bandwidth (aka download speed), but this is NOT what I want to do.

Thank you!

---

### Post by TheFu on 2022-11-18
I have some hidden files that aren't shown to normal users, but automation sees. Whenever those files are grabbed, I block the IP for a week by adding it to my ipset rules.  Currently, there are about 8000 active subnets here being blocked for that reason.  ipset rules translate into a single 'iptables' DROP firewall rule that is crazy efficient to process.  Somewhere above 200 iptables rules, I found the processing to slow. Best to avoid that.

BTW, it is best to not have any links that are available from a top level page (somehow) to the page with those files. If they are, web-crawlers WILL find them.  About 15 yrs ago, I started blocking based on user-agent.  
```
   if ($http_user_agent ~* "Baiduspider") { return 403; }
```
is an example.  Made that decision after Baidu was abusive to my servers, but when I looked at the analytics, ZERO visitors had Baidu as a referrer.  I also block really-old claimed browsers and referrers using some URL shorteners.  Over time, the block list has grown to about 200 things just the webserver handles BEFORE deciding to provide access.  For images, if the referrer isn't one of my webapps, direct requests get blocked. 
And for some static content, a completely different server with a larger cache is used.  That server has read-only access to an NFS mount, so if the box does get cracked, they won't be able to modify any of the static content.

As for doing what's in the thread subject - the only way I know to do that is by adding and removing DROP rules to the firewall during the periods you don't want to allow access.

---

