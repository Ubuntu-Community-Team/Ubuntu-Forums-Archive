---
title: "Web browsing on my netbook is driving me mad. You?"
date: 2011-04-10
forum: The Cafe
---

### Post by spupy on 2011-04-10
Forgive me if this is not the appropriate subforum - this is less of a request for help and more of a question to other users and how they do.

I got 3 OSs on my netbook: some XP I don't use, Ubuntu 10.10 and 11.04. I use mostly the 11.04 nowadays, but before Alpha 3 came I was always using the 10.10.

While special effects and videos (up to 720p) run with no problem on my netbook (HP mini 311c, 1.6GHz Atom, 2GB RAM, Nvidia ION), loading webpages is so slow that I want to punch the screen. Both Chromium/Chrome and Firefox 3/4 do this.

Say I'm browsing the forums, and ctrl+click several links to open them in new tabs. So the links in the tabs start loading and the browser starts freezing. I can barely scroll and click new links until everything is loaded! I understand that it's perhaps a limitation of the single core of my processor, but in similar scenarios other programs just slow down and don't lock up. It's infuriating. I remember this happening with my previous laptop as well, one that also had a single core.

So, fellow single-core laptop/netbook users, are you experiencing this? How are you coping?

---

### Post by mamamia88 on 2011-04-10
just installed debian testing on my netbook yesterday.  runs great.  ubuntu was getting too bloated.

---

### Post by PhilGil on 2011-04-10
Have you established that's it's a resource problem and not a wireless issue? Do you have the same issues on every wireless network you connect to? Have you tried to connect using an Ethernet cable?

Assuming it's a system resource problem, you could try a lighter weight distro. Like mamamia88, I'm running Debian (stable, in my case) on my netbook. It is noticeably peppier than Ubuntu. I've also run Lubuntu and noticed a significant performance increase.

The primary design goals of netbooks are low cost and long battery life, hence they are limited in resources. At the end of the day, you may have to learn to work with a netbook differently than you would with a regular laptop or desktop.

---

### Post by fuduntu on 2011-04-10
> **spupy said:**
> Forgive me if this is not the appropriate subforum - this is less of a request for help and more of a question to other users and how they do.

I got 3 OSs on my netbook: some XP I don't use, Ubuntu 10.10 and 11.04. I use mostly the 11.04 nowadays, but before Alpha 3 came I was always using the 10.10.

While special effects and videos (up to 720p) run with no problem on my netbook (HP mini 311c, 1.6GHz Atom, 2GB RAM, Nvidia ION), loading webpages is so slow that I want to punch the screen. Both Chromium/Chrome and Firefox 3/4 do this.

Say I'm browsing the forums, and ctrl+click several links to open them in new tabs. So the links in the tabs start loading and the browser starts freezing. I can barely scroll and click new links until everything is loaded! I understand that it's perhaps a limitation of the single core of my processor, but in similar scenarios other programs just slow down and don't lock up. It's infuriating. I remember this happening with my previous laptop as well, one that also had a single core.

So, fellow single-core laptop/netbook users, are you experiencing this? How are you coping?

Video playback and glitzy OpenGL tasks are offloaded to the GPU, page rendering however is handled by your CPU so you will probably see slowdowns during rendering of multiple pages.  That's one of the drawbacks of the Atom CPU.

---

### Post by frankbooth on 2011-04-10
I run Lubuntu on my netbook, doing day-to-day work (email, browsing, music, documents) and it runs just as smooth as my desktop.

As the user above said, if it's a resource problem, give Lubuntu or some other lightweight distro a go.

---

### Post by Madskillzz on 2011-04-10
Netbook Remix,  Dell mini 1018 i hate it these things would benefit from a higher resolution imo 1080p or sumtin.

---

### Post by ssam on 2011-04-10
did you have disk encryption enabled? i found that slowed down firefox. i also recommend disabling flash (or installing flash block which replaces flash files with a play button, so that you can play the ones you want.)

---

### Post by matty abbo on 2011-04-10
i have had the same problem with web browsing, being able to watch HD videos on youtube but web browser crashing on normal web browsing, when i applied updates to ubuntu it seemed to have stoped

---

### Post by HermanAB on 2011-04-10
Do yourself a favour and max out the RAM.

---

### Post by stmiller on 2011-04-10
I put a cheap 32GB SSD in my netbook. Still not that cheap, but makes overall performance very good now.

Chrome seems to run faster than Firefox (even Firefox 4) for me as well.

---

### Post by Plumtreed on 2011-04-10
I have been using PeppermintICE combined with web-based apps on a eeePC701...512RAM...it works fast and cleanly...small install, fast boot....browsing with this combination is not driving me mad, in fact, the small size makes it very portable,flexible and a pleasure to use.

---

### Post by LowSky on 2011-04-10
At least you have ION. I'm running a first gen with intel graphics.

Forget video anything on it.

I usually use it for note taking and email.

---

### Post by kiddfroster on 2011-04-10
> **LowSky said:**
> At least you have ION. I'm running a first gen with intel graphics.

Forget video anything on it.

I usually use it for note taking and email.

My netbook is fine, and it has Intel graphics. No slowdowns that aren't unreasonable, even with Compiz turned on. To the OP, have you tried clearing your cache. Even on my main laptop, which is highly specked, sometimes browser slowdowns are caused by a full cache.

---

### Post by kerry_s on 2011-04-10
perhaps your just opening to many tabs?

---

### Post by user1397 on 2011-04-10
> **spupy said:**
> Forgive me if this is not the appropriate subforum - this is less of a request for help and more of a question to other users and how they do.

I got 3 OSs on my netbook: some XP I don't use, Ubuntu 10.10 and 11.04. I use mostly the 11.04 nowadays, but before Alpha 3 came I was always using the 10.10.

While special effects and videos (up to 720p) run with no problem on my netbook (HP mini 311c, 1.6GHz Atom, 2GB RAM, Nvidia ION), loading webpages is so slow that I want to punch the screen. Both Chromium/Chrome and Firefox 3/4 do this.

Say I'm browsing the forums, and ctrl+click several links to open them in new tabs. So the links in the tabs start loading and the browser starts freezing. I can barely scroll and click new links until everything is loaded! I understand that it's perhaps a limitation of the single core of my processor, but in similar scenarios other programs just slow down and don't lock up. It's infuriating. I remember this happening with my previous laptop as well, one that also had a single core.

So, fellow single-core laptop/netbook users, are you experiencing this? How are you coping?Weird that you posted this, I was about to do the same...we seem to have the exact same issue! :(

---

### Post by Copper Bezel on 2011-04-10
I use Opera with Flash on-demand, which is like the Firefox Flash block in replacing Flash applets with buttons to load them at will. My netbook started with a 1.6Ghz processor and 32 GB of flash memory, and I upgraded the RAM to 2GB. I'm also using CompizStandalone instead of a full Gnome environment.

It's damned peppy. = )

---

### Post by lancest on 2011-04-10
AMD netbooks are better with HD video.

---

