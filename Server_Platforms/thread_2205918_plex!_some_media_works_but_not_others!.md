---
title: "plex! some media works but not others!"
date: 2014-02-16
forum: Server Platforms
---

### Post by cowboy3 on 2014-02-16
ok so i have installed Ubuntu server 12.04 amd64 on a desktop computer,  got plex, webmin, and restricted extras installed.  when i access plex  from either my laptop or a roku, about half the media will play but the  rest it tells me "were unable to play this video, make sure the server  is running and has access to this video".  all the media is in one  folder on one drive mounted via fstab. my problem is why will some of  the media play and the rest not. my first thought was that the server  didnt have the correct codecs available to do the transcoding and that  the stuff that worked was being direct streamed with no transcoding.

so  i installed restricted extras and even restarted the server. still  unsolved.  when i ran the plex server from Ubuntu 12.04 desktop,  winxp,  and Ubuntu 10.04 desktop it has worked flawlessly as far as transcoding  and transmitting just a hell of a lot slower.  so my next thought is  permissions. could several folders within a folder have different  permissions set?  And most of all how do i rectify this in ubuntu  server? or better yet how do i get plex to not care who's files what's?

so the media is three folders deep on sda2 auto mounted via fstab.
the server is running from sdc2

take it easy on the tard over here and thank you in advance!

---

### Post by tripp98 on 2014-02-16
Does the meda you are wanting to view show up on the plex interface after you do a scan? if it doesnt its a rights issue.

---

### Post by cowboy3 on 2014-02-16
nope it shows up, just wont play it.

---

### Post by greyday on 2014-02-18
Could be a connections issue (I was having these from time to time; some stuff just wouldn't play, other stuff would play but rebuffer constantly).  Check and make sure your stream settings on both your PMS install (via the web interface) and your device (mine are ipad, roku 3, and PS3) are set to your network max; if you're running, like I am, though all gigabit connections, then the highest setting is fine.

Some of it could just be the encoding as well; check and make sure the files play on, say, VLC, and if they do then maybe try reencoding to Plex optimal specs (note--also helps with buffering issues; a 1080mkv will have buffering issues most of the time, reencoded to optimal plex specs as mp4, works like a charm).  Also make sure your hardware can handle the encoding, as running to, say, the Roku or ipad, generally the server is doing all the work.  Running through the PS3, it handles a lot of it.

And finally, make sure you have the most current version of Plex.  You probably researched this already, but the current repository (apt-get) version isn't the newest stable.  You can find simple download and install instructions with a quick google.

Plex on Ubuntu is amazing once it's working optimally (as you know, being able to access some already).  Good luck!

---

