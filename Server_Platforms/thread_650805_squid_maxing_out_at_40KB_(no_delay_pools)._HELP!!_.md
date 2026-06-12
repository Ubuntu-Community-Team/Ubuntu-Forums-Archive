---
title: "squid maxing out at 40KB (no delay pools). HELP!! = )"
date: 2007-12-26
forum: Server Platforms
---

### Post by senoralastair on 2007-12-26
Hey there ubuntu-ers!
I've got a prob with squid that's really confusing me. I've been searching the forums and google for a couple of weeks with no result.
Here's my prob: I'm replacing our corporate proxy (squid) with an ubuntu box running squid (2.6.stable5). I've successfully joined it to the domain (using samba/winbind) and i've got squid authenticating properly.
I'm copying the delay_pool config across to the new server, but what i've found is that whether or not i've got the delay_pool section in the squid.conf, i'm being limited to about 40KB/s download speed! (so basically ignore delay_pools cos it's currently commented out).

Normally i'd average about 700KB/s, and this is downloading a speedtest file straight from our isp. (i've also tried downloading ubuntu iso's as well - same speed though).
So, i've checked through the squid.conf file and i can't find anything else that might be cutting my speed down. I also did a wget from that box, and was able to download the same speedtest file at normal speeds (600-700KB/s), so i've ruled out switch/network issues between the net and this proxy box, but i can't work out what is slowing me down so drastically.

I extracted all the non-comment entries from the current & my new squid proxies, and i can't see anything that's going to be affecting speed at all.

Does anyone have any ideas about what I can check next, as i'm pulling my hair out over this. 

thanks in advance! Hopefully some of you gurus can point to something that'll make my day!

cheers!

---

### Post by senoralastair on 2008-01-01
anybody?
does anyone have any ideas at all that i could try, or that i could have overlooked? there's bound to be some obscure (or even just a really basic) thing that i've just overlooked or need to tweak...
this is killing me... and if i don't get this sorted by the time my boss gets back from holidays, i know he's wanting to get rid of my linux box and replace the proxy with WINDOWS and ISA server!!!  we all know that no good could possibly come of that!! = P

any suggestions would be greatly appreciated, no matter how basic...

---

### Post by FoxOne on 2008-01-01
bump

---

### Post by FoxOne on 2008-01-01
I can't help you personally with this question, but I have a co-worker who might, he has a very similar setup, I'll shoot him a link to this post. He's running it in a school with no download performance issues.

---

### Post by senoralastair on 2008-01-01
oh thanks heaps... that'd be great!
= )

---

### Post by senoralastair on 2008-01-02
scratch scratch.... (that's the sound of me scratching my head still)....
haha.

still no love, i followed these instructions on profiling the squid server:
[http://wiki.squid-cache.org/SquidFaq/SquidProfiling](http://wiki.squid-cache.org/SquidFaq/SquidProfiling) but to no avail.

average output from iostat 1:
Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
cciss/c0d0        0.00         0.00         0.00          0          0

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           0.00    0.00    0.00    0.50    0.00   99.50

average output from vmstat 1:
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 1991672 130424 133224    0    0     0   240  199   96  0  0 99  0
 0  0      0 1991688 130424 133228    0    0     0     0  189  118  0  0 100  0

this is whilst running nagios and and sms-sending daemon as well. although i've tried shutting down nagios and only running squid, but still no go...

anybody anybody?

---

### Post by senoralastair on 2008-01-09
hey folks. i don't know if anyone is still looking at this, but i'm thinking it's a network card thing...
i've posted a new thread in networking:

[http://ubuntuforums.org/showthread.php?p=4105488#post4105488](http://ubuntuforums.org/showthread.php?p=4105488#post4105488)

---

