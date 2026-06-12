---
title: "Hardware requirements for (software) RAID5"
date: 2010-03-18
forum: Server Platforms
---

### Post by Donny Bahama on 2010-03-18
I've built a server with (intentionally) very low-power components. The motherboard uses a Via C3 CPU running at 700MHz. The server has 512MB of RAM and I'm running 8.04 Server Edition (no GUI). This is purely a file server - not a lot of daemons started (except the defaults) -- no web server, etc. Just NFS, Samba and Open SSH (for remote administration). I'm not sure how much free RAM it has (it's down at the moment).

Is the RAM/CPU going to be inadequate for running software RAID5? 

I've done some big rsyncs and even without RAID, this thing is pretty slow. I'm not terribly concerned about the write speed, but if the read performance is going to be inadequate for playing (not streaming - just playing) a 720p MKV movie over my LAN, then I need to rethink this.

Your input will be much appreciated. :)

---

### Post by jrssystemsnet on 2010-03-18
> **Donny Bahama said:**
> I've built a server with (intentionally) very low-power components. The motherboard uses a Via C3 CPU running at 700MHz. The server has 512MB of RAM and I'm running 8.04 Server Edition (no GUI). This is purely a file server - not a lot of daemons started (except the defaults) -- no web server, etc. Just NFS, Samba and Open SSH (for remote administration). I'm not sure how much free RAM it has (it's down at the moment).

Is the RAM/CPU going to be inadequate for running software RAID5? 

I've done some big rsyncs and even without RAID, this thing is pretty slow. I'm not terribly concerned about the write speed, but if the read performance is going to be inadequate for playing (not streaming - just playing) a 720p MKV movie over my LAN, then I need to rethink this.

Your input will be much appreciated. :)Nah, it ought to be OK.  mdraid5 doesn't really require any extra RAM to speak of.  The main reason the system will be perceptibly slow is that you don't have enough RAM to do any significant caching of the filesystem - but that's the same problem with or without the mdraid.

Read performance ought to be fine; worst-case scenario should be that it's not any better than single-drive performance.  More likely, you'll see a pretty significant boost over single-drive read performance, even with such a relatively wimpy host running it.  Write performance won't be bad for stuff like saving movies, either; you only really run into crippling issues with the read-modify-write fandango when you're doing a lot of random-access small writes.  This could in theory be a problem if you're doing a lot of bittorrenting directly to the server... but only in theory; in practice you're unlikely to be getting speeds from a few torrents that would really strain the hardware.

---

### Post by Donny Bahama on 2010-03-18
> **jrssystemsnet said:**
> Nah, it ought to be OK.  mdraid5 doesn't really require any extra RAM to speak of.  The main reason the system will be perceptibly slow is that you don't have enough RAM to do any significant caching of the filesystem - but that's the same problem with or without the mdraid.

Read performance ought to be fine; worst-case scenario should be that it's not any better than single-drive performance.  More likely, you'll see a pretty significant boost over single-drive read performance, even with such a relatively wimpy host running it.  Write performance won't be bad for stuff like saving movies, either; you only really run into crippling issues with the read-modify-write fandango when you're doing a lot of random-access small writes.  This could in theory be a problem if you're doing a lot of bittorrenting directly to the server... but only in theory; in practice you're unlikely to be getting speeds from a few torrents that would really strain the hardware.Excellent news! Thanks very much for the input! I had thought of trying to run rtorrent on the server, but it's a pretty low priority. I have a strong preference for legal media, so it's very rare that I download any torrents.

---

