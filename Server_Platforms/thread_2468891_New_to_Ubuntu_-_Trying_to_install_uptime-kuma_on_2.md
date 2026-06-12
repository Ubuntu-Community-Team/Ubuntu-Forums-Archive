---
title: "New to Ubuntu - Trying to install uptime-kuma on 20.04 with apache, help needed!"
date: 2021-11-13
forum: Server Platforms
---

### Post by ads2021 on 2021-11-13
Hey All, 

As I say - New to Ubuntu and I'm just playing to get the hang of things. 

I have installed 20.04 LTS and apache, ufw etc - got that all working and was able to post a simple .html out on the web with SSL, so that was all good!

 I wanted to install uptime-kuma which I have done but I'm having a problem getting that to go out on the web. The tutorial I followed for this was: [https://www.howtoforge.com/how-to-install-kuma-self-hosted-uptime-robot-alternative/](https://www.howtoforge.com/how-to-install-kuma-self-hosted-uptime-robot-alternative/)

It could be me and still a learning process, but it doesn't seem to follow the ```
/var/www/example-domain.com
``` process I was using when I posted my test page.

A little guidance would be appreciated if anyone has some time. :D

---

### Post by TheFu on 2021-11-13
I truly hope you aren't using SSL!!!  That has been non-secure for years.  Only TLS v1.3 or later should be used as of this date.
For non-trivial servers, ufw really doesn't provide sufficient firewall control.  You'll definitely want to learn iptables or firewalld.

I've never heard of uptime-kuma. Give me a second to   .... 
ok, it is something I wouldn't deploy on my network for a few reasons, mainly due to node.js (lots-o-baggage). I did find a youtube docker-install guide and the github project with reasonable installation instructions.

Sorry, I'm not more help.

You'll need to show each command run and the RELEVANT results here for anyone to help.

---

### Post by louislam2 on 2021-11-13
You probably need a reverse proxy setting for Apache. You could find more information on my wiki and help question in the repo.
[https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy](https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy)

---

### Post by TheFu on 2021-11-14
> **louislam2 said:**
> You probably need a reverse proxy setting for Apache. You could find more information on my wiki and help question in the repo.
[https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy](https://github.com/louislam/uptime-kuma/wiki/Reverse-Proxy)

If apache is being used, then a separate reverse proxy isn't necessary.  However, I 100% agree that a reverse proxy can be a great tool for many reasons like load balancing, reducing systems open directly to the internet, and for TLS termination as a front-end to multiple back-end servers.

Websites can be located almost anywhere on a web server. There's nothing magical about /var/www. It is the admin's choice.  So, posting a directory and thinking that magically tells us everything isn't the situation.  
In fact, in the early days of the internet, /var/ would never be used for files that lasted between boots.  /var was for temporary things.  I recall my shock-horror when Redhat packages were setup by default to point there. Seemed really foolish for many reasons.  At the time, typically, apache would be installed with all files under /usr/local/apache - that included all settings, binary programs AND website data.  Apache would be pulled as source code and we'd compile it, since the OS releases would be installed and likely not patched for years.  It was a different time.

TLS v1.2 warnings about the "Raccoon attack"
[LIST]
[*][https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/](https://threatpost.com/nsa-urges-sysadmins-to-replace-obsolete-tls-protocols/162814/)
[*][https://www.zdnet.com/article/nsa-urges-system-administrators-to-replace-obsolete-tls-protocols/](https://www.zdnet.com/article/nsa-urges-system-administrators-to-replace-obsolete-tls-protocols/)
[*][https://techthelead.com/the-nsa-upgrade-obsolete-tls-protocols-or-risk-another-massive-breach/](https://techthelead.com/the-nsa-upgrade-obsolete-tls-protocols-or-risk-another-massive-breach/)
[/LIST]
I know a little about Raccoons!
> Bad news: there’s a vulnerability in TLS 1.2. Good news: researchers say it’s “very hard to exploit” and major vendors have already released security patches for it.
But there's also the fact that certain govts, known for hacking world-wide, don't allow TLS v1.3 to be used crossing their country-wide firewall. Basically, they force their residents to use TLS v1.2 or earlier.  When I learned that over a year ago, I immediately switched all my websites to TLS v1.3 - the attacks dropped about 90%. It was the single most useful thing I did for security of my websites - well, besides having automatic, daily, versioned, "pulled" (never pushed!), backups. That is always my #1 security solution.  

Just for clarity, SSL/TLS doesn't actually "secure" a website. It just makes the content of the data transferred come unmolested and provides some opportunity to know the server is really the server.  But in the days of nations running DNS and CAs, even that 2nd thing isn't assured for every client. Anything more isn't guaranteed, just luck.  Michael Lucas gave a talk about TLS in 2021: [https://www.youtube.com/watch?v=eRWbNno4sN4](https://www.youtube.com/watch?v=eRWbNno4sN4)

---

