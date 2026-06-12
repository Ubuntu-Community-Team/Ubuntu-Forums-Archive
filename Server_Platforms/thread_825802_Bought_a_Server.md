---
title: "Bought a Server"
date: 2008-06-11
forum: Server Platforms
---

### Post by xiownthisplacex on 2008-06-11
Hi all. I bought an ubuntu server 7.10 today, and installed rtorrent. The net connection is 100 mbs shared and i was able to download already at 4000 kbs/s, but upload doesn't pass 500 kbs/s. Do I have to like open a port, or turn off firewall or something in order to let connections in better? Sorry for this question, but I really don't know. Thanks in advance.

---

### Post by mbeach on 2008-06-11
do you get faster speeds from other machines on that network?

It could simply be your isp throttling your serving of torrents.  Topic in the news lately:
[http://www.financialpost.com/story.html?id=515048](http://www.financialpost.com/story.html?id=515048)

---

### Post by xiownthisplacex on 2008-06-11
i wouldn't know, because i only have that machine that i bought..
my server host says that the server is in Amsterdam, but didn't say the isp..

---

### Post by hyper_ch on 2008-06-11
have you throttled the upload?

On the bottom left you have

[Throttle XX / YY]
XX --> Upload in kilobytes
YY --> Download in kilobytes
Off --> no limit

Btw, I'd suggest to get the latest SVN version,made a little howto for it - because that one features DHT.

---

### Post by xiownthisplacex on 2008-06-11
in my .rtorrent.rc i have no limits what so ever, i used this howto [http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon](http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon) and Throttle is off/off
so i really dont know the problem here..

---

### Post by hyper_ch on 2008-06-11
that's my little howto ;) do you ahve DHT activated?

Might it be that there are not many leechers for those torrents?

---

### Post by xiownthisplacex on 2008-06-11
great howto!
i have dht disabled, because i am obligated to have it off, since i use a private tracker and there are now 319 leechers at the moment, and it is sending at 91 kbs/s :(

---

### Post by hyper_ch on 2008-06-12
private trackers are evil ;)

Have a look at the peers screen and see if they are interested from downloading from you and what their speeds is.

---

