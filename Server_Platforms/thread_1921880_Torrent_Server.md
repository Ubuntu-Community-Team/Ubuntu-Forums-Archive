---
title: "Torrent Server"
date: 2012-02-07
forum: Server Platforms
---

### Post by bubylou on 2012-02-07
I current have a deluge server running on 11.10 but would like to find a better replacement. I have been researching quite a few option already but nothing beets experience. I do like the ability to use a web GUI but if it really cam down to it i could make do without it. I'm also running on pretty limited hardware so being lightweight is a big plus. I had to set it so that only one torrent would be active at a time to avoid crashing deluge if i attempted do do any other big tasks on the server. Transmission seems to be my first choice at the moment. Torrent flux was another but it requires PHP. So I'm looking for efficiency, plenty of features and having a pretty web GUI would be nice. Let me know what you think.

---

### Post by snowpine on 2012-02-07
You may find this how-to interesting:

[http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

rtorrent is definitely "lightweight." :)

---

### Post by arrrghhh on 2012-02-07
I went rtorrent+rutorrent after messing with a LOT of different solutions (torrentflux+b4rt, deluge, transmission, utorrent, etc). and it is by FAR the best setup I've ever had.

With rtorrent you get a lot of flexibility, but there's not a lot 'built-in'.  With addons like rutorrent tho, I'm missing nothing.

---

### Post by bubylou on 2012-02-07
I think i have narrowed it down to two now. Its either rtorrent + rutorrent or transmission. Any insight on transmission. ru torrent seems to offer more features but transmission was very easy to set up but ill probably give rtorrent a try.

---

### Post by arrrghhh on 2012-02-07
> **bubylou said:**
> I think i have narrowed it down to two now. Its either rtorrent + rutorrent or transmission. Any insight on transmission. ru torrent seems to offer more features but transmission was very easy to set up but ill probably give rtorrent a try.

You hit the nail on the head.

If you want flexibility/configuration options/plugins out the wazoo go rutorrent.  If you want ease of setup, go Transmission.

rtorrent is going to consume WAY less resources.  It's worth the pain to setup ;).

---

### Post by bubylou on 2012-02-07
could you list some of your favorite plugins and features of rtorrent. im not completely sold on it yet but im working on installing it now. Another thing that concerns me is that rtorrent doesn't seem to be actively being developed.

---

### Post by arrrghhh on 2012-02-07
> **bubylou said:**
> could you list some of your favorite plugins and features of rtorrent. im not completely sold on it yet but im working on installing it now.

Hrm, I think all the plugins/addons I use are from rutorrent.  Let me see...

EraseData - right click option for remove AND delete data
Create - create torrents
Traffic - see traffic stats
RSS - RSS feed built into rutorrent
Edit - edit trackers
Throttle - change individual torrent groups to get individual throttle settings...
Scheduler - set times of day/throttle plans
AutoTools - looks awesome, haven't set it up yet...
GeoIP - c'mon that's just fun :p
Ratio - for setting ratio groups!
Show Peers like wTorrent - took me a while to figure this one out, but I didn't like how peers were shown by default...
SeedingTime - self-explanatory ;)
DiskSpace - this one too :p
Unpack - another cool one I just found looking thru the list!
CPU Load - shows load of the server in rutorrent semi-real-time.
Extsearch - adds search functionality within rutorrent

And believe it or not that's not all of 'em.  Don't be fooled either, this doesn't mean that rutorrent doesn't include a lot of features - these were just 'missing' and were added with plugins by the community ;).

Honestly as far as why I use rtorrent after trying the rest - it simply works pretty much flawlessly once it's setup correctly.  It was quite a pain to get it flawless, but once I did... WAY better than ANY other solution out there.  I'm just really picky is what it boils down to, and I like having options.  Lots of options :D.  Transmission was just too... simple.  It was pretty/elegant, but not *functional*.  torrentflux/+b4rt never worked right, and spawned processes like crazy.  It was a mess/hodgepodge.

rtorrent+rutorrent is very slick, once you get over the pain of installing and setting it up ;).

---

