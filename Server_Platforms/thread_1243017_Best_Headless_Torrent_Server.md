---
title: "Best Headless Torrent Server"
date: 2009-08-17
forum: Server Platforms
---

### Post by quietas on 2009-08-17
**_What is the best torrent server for Ubuntu?_**

_**Features**_
[LIST]
[*]Headless (background daemon mode)
[*]Web GUI
[*]Clean Interface
[*]Speed
[*]Upload Torrents also
[*]Private Trackers
[*]Current Development
[*]Move on Completion
[*]Low System Resources
[/LIST]

I've used Transmission (current), Deluge, Torrentflux, Vuze, and Rtorrent/Wtorrent. Each has benefits, but they all seem to have drawbacks.

It needs to be headless with a web front end and it needs to be relatively easy. My wife also uses this to download TV shows and simplicity counts highly.

I've been planning to rebuild my home server, it's main function is to download torrents and then serve them up via samba for my Windows machines and XBMC clients (Apple TV's and Xbox's). It also serves as a repository for all my music, game isos, dvd rips, and the rest of misc files I don't want to store on my laptops.

---

### Post by Thirtysixway on 2009-08-17
What do you not like with existing systems?  I use torrentflux and it seems pretty straight-forward to me.

You could go about rewriting or redoing parts of torrentflux or similar applications if you have the knowhow.  The only part I see torrentflux not doing is the move on completion, although you could map a folder to the downloads folder of torrentflux as to create the illusion it's been moved.

I know uTorrent has a web interface, but I've only tried the Windows version with limited success (it's also been a while, so newer versions may have improved.)

---

### Post by quietas on 2009-08-17
Torrentflux has seperate processes for every torrent. I often download 20 things at once, thus is runs 20 instances of bittornado. Web interface was hard to navigate.

Transmission has issues with Demonoid and other private trackers. Stats reporting is bad and often won't download the .torrent file correctly.

Deluge was clunky to set up. Worked mostly, wife had issues though. Daemon mode took some work to make work.

Rtorrent with Wtorrent GUI worked, lowest recources by far. But I used it months ago and I can't remember what I did not like on it.

Vuze/Azueus was a bit wonky to get started. Java based and it used mroe resources than it should like it's windows based counterpart.

I guess I'm looking for opinions on what is the best middle ground and maybe recommendations to new servers or features I missed in the ones I listed.

---

### Post by quietas on 2009-08-17
Heaven forbid, I'd even consider Windows Home Server for the singular reason that it can run uTorrent. =)

---

### Post by doogy2004 on 2009-08-17
I used to use Azureus/Vuze with the HTMLwebUI, I would set my torrents to download in a temp folder then upon completion move to their final destination.  I ran this setup on a 1Ghz frankenstein computer (parts from everywhere), it was more than capable of running at least 30+ torrents at a time.  We would then stream the downloaded files to our xboxs and other media devices throughout the house.  Again all on a 1Ghz pc with 512MB of ram with 4 active users.

---

