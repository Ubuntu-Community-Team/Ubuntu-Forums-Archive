---
title: "Need help with 12.04 post-upgrade issues"
date: 2012-05-10
forum: Server Platforms
---

### Post by stangri on 2012-05-10
I've been staying with 10.04 for a while and have recently used the built-in upgrade utility to upgrade my server first to oneiric and then to 12.04.

I'm now presented with two problems which I would very much appreciate community help with.

1. Asterisk install. I've had it installed from the digium's repo in the past, but it doesn't have the binaries for 12.04 for some reason: [http://packages.asterisk.org/deb/dists/](http://packages.asterisk.org/deb/dists/) so I'm stuck with the oneiric binary in my system. There is the asterisk-1.8 in the main Ubuntu repo, but its version is older than what I have installed. Here's the package version info:
Package asterisk:                        
p   1:1.8.10.1~dfsg-1ubuntu1                      precise                   500 
i   1:1.8.11.1-1digium1~oneiric                                             100 

What should I do about that? Should I stay on oneiric version and wait until Digium updates its repo? Should I somehow migrate to the main repo version? How can I do it, keeping *all* of my asterisk settings?

2. Some services stopped auto-starting on system boot. I can however start them manually when I connect over ssh, but I would like them to be auto-started. I have this problem with asterisk, apache2 and svnserve.
I have googled and used the update-rc.d to recreate the symlinks in /etc/rc2.d (and I do have S20apache2, S20asterisk and S20svnserve there), but these services do not seem to auto-restart. When I ran the rcconf I can also see these services in the auto-start list, still they do not auto-start. 

Which log-file should I check for errors? Any help on how to restore the auto-start functionality?

PS. Not sure if it matters, but I have no conf-files for either of these services in /etc/init/. Should I have them? If so, where do I get them? 

Thanks!

---

