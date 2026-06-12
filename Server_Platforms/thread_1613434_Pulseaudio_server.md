---
title: "Pulseaudio server?"
date: 2010-11-04
forum: Server Platforms
---

### Post by l0xin on 2010-11-04
Does anyone know, or know of a guide, that shows how to set up Pulseaudio on the server, allowing it to stream audio over the network?

I've searched for ages, but can't find anything at all...

---

### Post by arnavk007 on 2010-11-04
Try subsonic it's a great media server

---

### Post by JDorfler on 2010-11-04
I don't know about subsonic, but I use mt-daapd server (firefly) for my Daap server and Mediatomb for upnp server.  Both are in the Ubuntu repository and are set up via webgui from client computers once installed on your server.

---

### Post by arrrghhh on 2010-11-04
I have yet another suggestion to throw into the hat.

I tried using pulse, and it was just too much of a PITA.  I would get it all setup & configured, then pulse would have some minor update that would break everything, and I was sick of it.

So now what I do is MPD - MPD plays music locally from my server, and then to stream it I use http.  The one problem I found with this is the audio isn't perfectly synced - so if it's in the same house and you play the music in multiple places at the same time & can hear them all it is noticable.

I also use Firefly, but it can be cumbersome with a large library.  It also doesn't do streaming from a central server if you want all the music in sync.  Subsonic looks interesting, but I can't quite figure out how to enable streaming on it.

---

### Post by JDorfler on 2010-11-04
> **arrrghhh said:**
> 
I also use Firefly, but it can be cumbersome with a large library.  It also doesn't do streaming from a central server if you want all the music in sync.  Subsonic looks interesting, but I can't quite figure out how to enable streaming on it.

If you don't mind me asking, but I use firefly with over 18,000 files and I have yet to see a problem.  However, I do have a 4 core processor with 4 Gigs of ram on my media-server.  I was wondering if your problems are due to FireFly or due to hardware.  You mind telling me what you are using as your server to see if I can find to see if I experience the same problems?

---

### Post by arrrghhh on 2010-11-04
> **JDorfler said:**
> If you don't mind me asking, but I use firefly with over 18,000 files and I have yet to see a problem.  However, I do have a 4 core processor with 4 Gigs of ram on my media-server.  I was wondering if your problems are due to FireFly or due to hardware.  You mind telling me what you are using as your server to see if I can find to see if I experience the same problems?

I have about 80,000 songs.  My server used to be pretty bare-bones, but I just recently upgraded to a quad-core proc - haven't tried it since then.

With that said, it wasn't unbearable - I just found it was easier for the client machines to point to a share and 'cache' the library locally.  Now obviously the songs themselves are still on the server, but whatever your music app of choice is stores the information so it's more quickly accessible.  It seems everytime I would try to access Firefly, it would re-create the whole list - and this would take some time.  It wasn't like 30 minutes, but the difference between a few seconds to pull up all the songs & 30 seconds seems like an eternity to most end-users :p

Also maybe we should talk network architecture - my server is on a gigabit LAN, but the clients are all wireless G.

---

### Post by arnavk007 on 2010-11-05
What do you mean by streaming
subsonic works like a website
you login into It cluck on the play button on the song of your choice and listen to the song

---

### Post by arrrghhh on 2010-11-05
> **arnavk007 said:**
> What do you mean by streaming
subsonic works like a website
you login into It cluck on the play button on the song of your choice and listen to the song

I want subsonic to play both streams and locally.  I had issues with it, although it works fine on my phone - which is really why I setup subsonic.  MPD works great for me as a local/HTTP streaming tool.

---

### Post by JDorfler on 2010-11-06
> **arrrghhh said:**
> I have about 80,000 songs.  My server used to be pretty bare-bones, but I just recently upgraded to a quad-core proc - haven't tried it since then.

With that said, it wasn't unbearable - I just found it was easier for the client machines to point to a share and 'cache' the library locally.  Now obviously the songs themselves are still on the server, but whatever your music app of choice is stores the information so it's more quickly accessible.  It seems everytime I would try to access Firefly, it would re-create the whole list - and this would take some time.  It wasn't like 30 minutes, but the difference between a few seconds to pull up all the songs & 30 seconds seems like an eternity to most end-users :p

Also maybe we should talk network architecture - my server is on a gigabit LAN, but the clients are all wireless G.

I gotcha.  80K songs is a bit.  I'm not sure if my network would get that big.  Right now most of my network is split in two.  One half is by the main satty modem and router in my work office and that's running on good old fashioned fast ethernet.  However, I had bridge the bulk of my network via RF LOS to our living quarters.  From here it is also on fast ethernet, but it will soon be a Gig as soon as the dumb switch gets here.  This area is where most of our personal systems, my media-server, and my main server are.  I do have it set up on my media-server if you want to cache the music and movies via Samba, it isn't an issue.  So far I'm not getting any complaints on service or any other issues.  Of course unless I cause them.

---

### Post by arrrghhh on 2010-11-06
> **JDorfler said:**
> I gotcha.  80K songs is a bit.  I'm not sure if my network would get that big.  Right now most of my network is split in two.  One half is by the main satty modem and router in my work office and that's running on good old fashioned fast ethernet.  However, I had bridge the bulk of my network via RF LOS to our living quarters.  From here it is also on fast ethernet, but it will soon be a Gig as soon as the dumb switch gets here.  This area is where most of our personal systems, my media-server, and my main server are.  I do have it set up on my media-server if you want to cache the music and movies via Samba, it isn't an issue.  So far I'm not getting any complaints on service or any other issues.  Of course unless I cause them.

Dang man you've got a pretty interesting/unique network setup!  Mine's much simpler :p  Plus, I'm very impatient, especially with the music.  I just want to click a song, and hear it play.  Honestly most of the music I listen to is played locally out of the server, so I just use [MPD](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)+alsa+[MPM](https://addons.mozilla.org/en-US/firefox/addon/6324/).  MPM is amazing BTW if you've never used it!  2.0 is awesome!

A little OT with a little on-topic stuff ;)

---

### Post by JDorfler on 2010-11-06
> **arrrghhh said:**
> Dang man you've got a pretty interesting/unique network setup!  Mine's much simpler :p  Plus, I'm very impatient, especially with the music.  I just want to click a song, and hear it play.  Honestly most of the music I listen to is played locally out of the server, so I just use [MPD](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki)+alsa+[MPM](https://addons.mozilla.org/en-US/firefox/addon/6324/).  MPM is amazing BTW if you've never used it!  2.0 is awesome!

A little OT with a little on-topic stuff ;)

I run 3 networks for work, 1 network for play (the one I'm using now and is mine), and a good old fashioned dail-up phone system.  Not too shabby for a straight trunk level data guy.  I'll take a look at MPM.  If it speeds things up, why not?

---

### Post by arrrghhh on 2010-11-06
MPD is extremely flexible - and just like rtorrent runs without a GUI, very small footprint, any interface connects to the backend mpd process.  Very cool - so many audio output options as well.

---

### Post by arnavk007 on 2010-11-07
> **arrrghhh said:**
> MPD is extremely flexible - and just like rtorrent runs without a GUI, very small footprint, any interface connects to the backend mpd process.  Very cool - so many audio output options as well.
looks like we are fighting while Ioxin is not interested.
BTW i have only 300 songs
pretty small
everything works extremely fast

---

### Post by arrrghhh on 2010-11-07
> **arnavk007 said:**
> looks like we are fighting while Ioxin is not interested.
BTW i have only 300 songs
pretty small
everything works extremely fast

Nobody is fighting...  Just talking about what we use and what works for us.  It's how I learn about new things and other options out there.

---

