---
title: "Headless Server 8.04 Transmission"
date: 2009-03-11
forum: Server Platforms
---

### Post by MrWES on 2009-03-11
Can someone point me to the correct syntax for the settings.sjon file to set share ratios when seeding?

[Update] -- found out transmission-cli won't support that until version 1.60

Thanks,
Bill

---

### Post by hyper_ch on 2009-03-11
you could use rtorrent instead.

---

### Post by MrWES on 2009-03-11
> **hyper_ch said:**
> you could use rtorrent instead.

rTorrent is cli only? and has a web interface? I'm running from a headless server.

Bill

---

### Post by hyper_ch on 2009-03-11
rtorrent is cli only... for a wui you'll need to compile it with xmlrpc support... however I just use it by ssh terminal

---

### Post by MrWES on 2009-03-11
> **hyper_ch said:**
> rtorrent is cli only... for a wui you'll need to compile it with xmlrpc support... however I just use it by ssh terminal


Yah I was just reading up on using rtorrent with screen; which would be fine. I also like the fact that is has a watch folder and ratio features. I didn't see it had a daemon. But I guess if I have it running with a detached screen and a watch folder I wouldn't need that.

I have transmission running, and I can add the .torrents via the web gui, but it doesn't have ratio settings nor a watch folder. But I guess you can script that.

Thanks again,
Bill

---

### Post by hyper_ch on 2009-03-11
rtorrent is nice... it was wuis - I never used one

but I'd recommend to compile from svn anyway as the 8.04 version is way beyond. However the current svn version needs an upgraded libcurl library (isn't that complicated).

Also you can add a feature that still missing from the current svn release - individual throttling of torrents.

And you get of course the usual confort:

having multiple watch folders where you just can pump .torrent files into and then based on those watch folders you can move around completed torrents... you have ratios...

It has no independant daemon but there's a script to run it at bootup (debian init script). I start it always manually in screen

:)

---

### Post by MrWES on 2009-03-11
I've never used any svn packages, is there a repository I add to beable to download their version of rtorrent?

Bill

---

### Post by hyper_ch on 2009-03-11
I wrote a howto for svn install of rtorrent - but you need to update libcurl

---

### Post by MrWES on 2009-03-11
> **hyper_ch said:**
> I wrote a howto for svn install of rtorrent - but you need to update libcurl


Where can I lay my hands on that HOWTO and libcurl?

Bill

---

### Post by firefly2442 on 2009-03-12
torrentflux is another option for a web-based bittorrent client.

---

### Post by hyper_ch on 2009-03-12
here's the howto for rtorrent:  [http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron](http://www.howtoforge.com/compile-rtorrent-from-svn-ubuntu-8.04-hardy-heron)

As for libcurl... I don't remember... I think I downloaded the source and compiled it on my on... google provided the answer.

Here's another howto with rtgui:  [http://www.howtoforge.com/how-to-configure-rtgui-for-rtorrent](http://www.howtoforge.com/how-to-configure-rtgui-for-rtorrent)

---

