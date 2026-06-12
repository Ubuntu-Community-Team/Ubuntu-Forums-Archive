---
title: "xen autostart VMs"
date: 2012-07-08
forum: Virtualisation
---

### Post by haggis444 on 2012-07-08
12.04 x64 server as my Dom0 with 4.1.2 xen install (all fresh and current as of yesterday). I changed the toolstack to xl as recommended.  

I cannot for the life of me figure out how to get my VMs to start when the machine boots.  I created my VM (DomU) cfg files in /etc/xen and then created a sym link to them under /etc/xen/auto but they do not autostart.  I can't seem to find a log showing what xend is doing either, although I haven't dug to deep on that. 

Any help would be appreciated.

_________________________________

OK, so I figured it out.  I read (although did no substantiate it) that xl is not quite ready for prime time, so I switched back to xm, and it worked!
 
I noticed in /var/log/boot.log this message, so this clued me into look at going back to xm:

```
Starting auto Xen domains: mc1.cfg ERROR: A different toolstack (xl) have been selected!
```

So maybe when 4.2 comes out I will try again with xl.

---

