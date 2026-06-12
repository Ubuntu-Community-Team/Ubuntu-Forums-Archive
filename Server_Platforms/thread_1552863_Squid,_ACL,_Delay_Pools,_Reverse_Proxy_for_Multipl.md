---
title: "Squid, ACL, Delay Pools, Reverse Proxy for Multiple Webservers"
date: 2010-08-14
forum: Server Platforms
---

### Post by shoaibi on 2010-08-14
I am trying to learn squid so that i can configure it to do:

[LIST=1]
[*]Define Content groups, e.g.
[LIST]
[*]images containing gif, png, ico, jpg, jpeg, etc
[*]Audio containing mp3, wav, ogg etc
[*]Video
[*]Archives
[*]Binary files
[/LIST]
[/LIST]

[LIST=1]
[*]Acting Reverse Proxy for Multiple Web Servers hosted at different geographical locations, accessible via static IPs.
[LIST]
[*]Restrict the amount of monthly Bandwidth to say 1G and if a site goes over it, all requests will go to original server.
[*]Restrict/Allow specific content groups from certain web servers.
[/LIST]
[/LIST]

I know (1) can be done with ACL and (2) can be done by

[LIST=1]
[*]Including files that belong to those web server's squid configuration in squid.conf (We can do it on one squid.conf but i like configurations to be distributed among files for easy management)
[LIST]
[*]Content groups can be allowed/denied using ACL in web-server specific files.
[*]Place Delay Pools restriction inside web-server specific files
[/LIST]
[/LIST]

But thats all theory. I have been trying to learn the syntax, and its seems so confusing, not to mention squid.conf is well documented but bloated for a new person, every line has 8 new tunnel openings to decide from.

Also can web-server specific config allow override parameters from the original squid.conf? Like say if i block everything e.g. images, audios, videos, binaries in squid.conf, can i allow specific content groups for specific web servers?

---

