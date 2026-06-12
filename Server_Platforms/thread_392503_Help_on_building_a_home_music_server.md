---
title: "Help on building a home music server"
date: 2007-03-24
forum: Server Platforms
---

### Post by stalefries on 2007-03-24
So, I'm planning on taking this old laptop and converting it into a home music server. I've tried searching around, but nothing has seemed to hit exactly what I want. 
The plan is to hook it up to our sound system at home, and possibly the TV, too. WiFi too, of course. Here's what I'm looking for:
[LIST]
[*]**Required:**
[*]iTunes (daap) server
[*]some sort of remote playlist tweaking (ie, connect to the server in some fashion and tell it what to play _on the sound system_. This could be a web interface or some sort of VNC or something.
[*]**Optional:**
[*]TV interface, perhaps a "Now playing" display, or even some sort of control. This could be the same as the second requirement above.[/LIST]Of course, a couple of these depend on whether I decide to use X display or not. 

Any suggestions would be appreciated. If you have any ideas on how this could be improved, I'd love that too. 

Note: I've already looked a little into mpd, and that might be able to solve most of this, but I would prefer not to have a client that depends on X, saving space for music.

---

### Post by Mr. C. on 2007-03-24
Consider "slimserver" by SlimDevices, now owned by Logitech.

No TV interface.

Server is open source, it can stream music anywhere, has software players, and outstanding hardware players.

[http://www.slimdevices.com](http://www.slimdevices.com)

MrC

---

### Post by stalefries on 2007-03-26
Mr C: that looks good like it could work as an alternative to the daap server thing, but I don't think it's exactly what I'm looking for.

---

### Post by Mr. C. on 2007-03-26
That's cool.

What requirements weren't met ?

MrC

---

### Post by erwall on 2007-03-27
Check out [http://www.mp3act.net](http://www.mp3act.net)

Can stream to anything that can connect to a url for a playlist.  Winamp, iTunes, XMMS, etc.

Users can have they're own playlists and options.  Needs apache, php, mysql.  Also, uses a slick AJAX interface.

I've been using it for a while now and it's been great.  Currently have 8000 songs in it.  Downside is your id3 tags have to have at least artist, title, and album values.

---

### Post by wayne_za on 2007-04-01
Take a look at jinzora, I had a few MP# in my collection and turned them into a full streaming media site.

Works very well, some great features.

[http://www.jinzora.org/](http://www.jinzora.org/)

---

### Post by stalefries on 2007-04-05
Wow, totally forgot about this. MrC, I really don't want to have to install client software specifically for this, we already have to have iTunes installed, so it's already there.

erwall, wayne_za, I think I've seen those, but I'll look at them again.

---

### Post by Mr. C. on 2007-04-05
No problem.  Slimserver streams fine to itunes.

MrC

---

### Post by stalefries on 2007-04-06
MrC: It does? That's weird, I guess I'll have to check again.

---

### Post by Mr. C. on 2007-04-06
[http://wiki.slimdevices.com/index.cgi?BeginnersGuideToiTunes](http://wiki.slimdevices.com/index.cgi?BeginnersGuideToiTunes)

---

### Post by wayne_za on 2007-04-06
See this external media server 300GB
Product features:
    * Stand-alone media player to playback MPEG-1, MPEG-2, DivX/Xvid, MP3, JPEG, media files 

[Media Server]("http://www.provantage.com/portable-multimedia-player-hv355u~220162457.htm")

[IMG]http://www.provantage.com/fullsize/hw162457.jpg[/IMG]

---

### Post by stalefries on 2007-04-08
Mr C: thanks for the link, I'll investigate.

wayne_za: I'm not interested in spending money on anything. I'm just trying to make this old laptop useful after I buy my new one.

---

### Post by Badjaccur on 2007-11-15
> **erwall said:**
> Check out [http://www.mp3act.net](http://www.mp3act.net)

Can stream to anything that can connect to a url for a playlist.  Winamp, iTunes, XMMS, etc.

Users can have they're own playlists and options.  Needs apache, php, mysql.  Also, uses a slick AJAX interface.

I've been using it for a while now and it's been great.  Currently have 8000 songs in it.  Downside is your id3 tags have to have at least artist, title, and album values.

mp3act is pretty cool. Too bad it seems like the developer abandoned it. Reason enough for Ben to for it into [GrammFone]("http://www.grammafone.com/")

---

### Post by victorbrca on 2007-11-15
> **wayne_za said:**
> Take a look at jinzora, I had a few MP# in my collection and turned them into a full streaming media site.

Works very well, some great features.

[http://www.jinzora.org/](http://www.jinzora.org/)

I use Jinzora as well. It's web based (PHP and SQL) and has an option for jukebox, an embeded flash player or download playlists (I think .m3u).

Their website has demos and a lot of users post links to their sites on the forum.

I have a how to on my blog in case u need (but the install is pretty straight forward) [**Link**]("http://wazem.blogspot.com/2007/06/organizing-all-your-audio-with-jinzora.html")


Vic.

---

