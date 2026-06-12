---
title: "IMO the perfect torrent client if you liked utorrent in windows"
date: 2010-11-16
forum: The Cafe
---

### Post by geoffmcc on 2010-11-16
Having come from a Windows background I find myself trying to find programs like the ones I use in Windows. I have been using utorrent for years and love it, but there was no linux version, like alot of things out there. 

Bare with me for a moment and i will get to the name of the client, or you can just skim to The Point.

No offense to anyone associated with the Transmission project, but I am not a fan, but at least if I open up a port on my router the client will do it's thing and give me a full connection. It has built it block list if you so choose so that's good, multiple downloads on a single port being forwarded (if i remember correctly) so that's good. The problem - all the errors about tracker not being allowed.

So I went looking for something else to use. I know (or i think i know) that utorrent is based off the bittorrnado project as I used that years back on windows before my switch to utorrent and thought the client to be the exact same. Searched the repository and found it. Went threw the config process setup port forwarding (by the way all of these have upnp options but dont seem to work for me on my router) and started to download something, no matter what I would get the yellow dot saying something wrong with connection.

So on to delluge. Found many people discussing it. Installed it and it works, Same problem with the connection, even though ports are forwarded but the speed is there. Also, it requires multiple ports to be forwarded for multiple downloads.

THE POINT:

Qbittorrent is exactly like utorrent. Has a different look to it but very similar and it has the feel. Didn't bother checking that upnp works, I just set it to one of the ports i had opened up for delluge and was finally given the green for a complete connection. I get the speed, the option to load a block list (would be nice to see built in update- but i dont think utorrent has that either) webui if so choose. Pretty much everything that utorrent has.

I searched the forums and there was a post from a couple years ago, someone saying it looked promising and another post from July of this year where someone had on there must download list. Just figured i would share my opinion with anyone willing to read it and get a post out there for people making the switch from Windows to Ubuntu.

---

### Post by lovinglinux on 2010-11-16
+ for qbittorrent

Is the fastest client I ever used. Simple to configure, with all the needed features. However, sometimes it stalls some torrents and I have to pause it, recheck and start again, otherwise it would go on downloading forever. Additionally, I have experienced problems with some torrents missing pieces. So, always re-check your torrents.

I was using qbittorrent for months, but recently I went back to Ktorrent, because of the UPnP plugin and the shutdown feature, that are very handy. Deluge was once my favorite client, but now I use Ktorrent or qBitTorrent.

---

### Post by themarker0 on 2010-11-16
Or just use Utorrent.

---

### Post by geoffmcc on 2010-11-16
> **themarker0 said:**
> Or just use Utorrent.

Im just picky. Although I am a fan of utorrent I am not a fan of using wine to run it.

---

### Post by Decatf on 2010-11-16
There is uTorrent Linux in the works. Last time I checked it was only a daemon with webui access. No word on an actual GUI yet.

---

### Post by czr114 on 2010-11-16
uTorrent is closed source, commercial, and should be avoided.

qBittorrent and Deluge are both good choices for avoiding Transmission. I'll never understand why they chose to bundle it in the first place.

---

### Post by _outlawed_ on 2010-11-16
> **themarker0 said:**
> Or just use Utorrent.

> **geoffmcc said:**
> Im just picky. Although I am a fan of utorrent I am not a fan of using wine to run it.

uTorrent in wine is currently buggy to all hell. It won't let you delete torrents after you complete them.

> **Decatf said:**
> There is uTorrent Linux in the works. Last time I checked it was only a daemon with webui access. No word on an actual GUI yet.

Can't wait for the linux native version! :D

> **czr114 said:**
> uTorrent is closed source, commercial, and should be avoided.

qBittorrent and Deluge are both good choices for avoiding Transmission. I'll never understand why they chose to bundle it in the first place.

+1 for Deluge, though Deluge does like to spam your router security logs to no tomorrow.

Ran Deluge over night seeding the Ubuntu torrents, and woke up 8 hours later with ~50,000 entries in the router security log from Deluge and incidentally my router had quit in the middle of the night too. lol

---

### Post by czr114 on 2010-11-16
Deluge, unfortunately, does get a bit sluggish with several hundred torrents open.

Neither of those clients have UTP support, which is a shame. Despite so much development time expended elsewhere, we can't seem to get it to something so basic as UTP support.

All in all, though, they're both still great software, and each one is a better choice than uTorrent, and especially uTorrent in WINE.

---

