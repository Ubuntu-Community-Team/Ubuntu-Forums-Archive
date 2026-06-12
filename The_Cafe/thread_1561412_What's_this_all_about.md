---
title: "What's this all about ?"
date: 2010-08-26
forum: The Cafe
---

### Post by Swagman on 2010-08-26
My Computer (running 10:04 32 bit) just went all "sticky" ie: Mouse really stuttering.

I shutdown and rebooted and it's fine. fired up Firefox to be confronted by an Xmarks update request. Would this have made the mouse "jerky"?

Just out of curiosity I went into the routers "logs" page and saw

```

Wed, 2010-08-25 08:18:47 - Administrator login successful - IP:192.168.0.4
Thu, 2010-08-26 06:39:59 - Send out NTP request to time-g.netgear.com
Thu, 2010-08-26 06:41:19 - Send out NTP request to time-h.netgear.com
Thu, 2010-08-26 06:43:29 - Send out NTP request to time-g.netgear.com
Thu, 2010-08-26 06:47:19 - Send out NTP request to time-h.netgear.com
Thu, 2010-08-26 06:54:29 - Send out NTP request to time-g.netgear.com
Thu, 2010-08-26 07:08:20 - Send out NTP request to time-h.netgear.com
Thu, 2010-08-26 07:35:30 - Send out NTP request to time-g.netgear.com
Thu, 2010-08-26 08:29:20 - Send out NTP request to time-h.netgear.com
Thu, 2010-08-26 10:16:30 - Send out NTP request to time-g.netgear.com
Thu, 2010-08-26 10:43:53 - Administrator login successful - IP:192.168.0.4

```

I've never seen that before. Why would my router be doing that ?

---

### Post by Swagman on 2010-08-26
Also.. Scrolling further back in the logs reveals

```

Sat, 2010-08-21 14:38:49 - UDP Packet - Source:213.248.117.222,3478 Destination:213.122.123.116,1033 - [DOS]
Sat, 2010-08-21 14:38:49 - UDP Packet - Source:96.17.157.56,3478 Destination:213.122.123.116,1033 - [DOS]
Sat, 2010-08-21 14:38:50 - UDP Packet - Source:213.248.117.222,3478 Destination:213.122.123.116,1033 - [DOS]
Sat, 2010-08-21 14:38:50 - UDP Packet - Source:124.40.51.158,3478 Destination:213.122.123.116,1033 - [DOS]

```

Does that mean someone's being having a crack at me ?

---

### Post by grahammechanical on 2010-08-26
DOS could mean Denial Of Service attack. It seems that three different sources are sending to the same destination (you?)

regards

---

### Post by lovinglinux on 2010-08-26
I have experienced issues with Xmarks before, specially during sync, so I haven't used if for a while.

My advice is to install [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/") and remove Xmarks. The reason to do that is that Firefox Sync is already incorporated by default into the latest Firefox 4 Beta. You won't need Xmarks anymore, unless you want to sync Firefox with Chrome. Besides, Firefox Sync can sync bookmarks, passwords, history, settings and tabs.

---

### Post by Swagman on 2010-08-26
Thanks for the replies guys.

+rep if we did it !!

---

### Post by Brunellus on 2010-08-26
The NTP requests are requests for Network Time Protocol--a means by which system clocks are synchronized over the Internet.

The other stuff marked DOS is probably some sort of Denial of Service Attack.  I was plenty annoyed once when I discovered that sort of traffic.  Hilariously, I ended up writing and publishing a law review article on that very topic (59 Cath. U. L. Rev. 527 (2010), for all you lawyers and law students out there).

The DOS attack might--MIGHT--slow your computer down, but the NTP traffic probably wouldn't.

---

