---
title: "Creating an Internet Radio Stream"
date: 2008-06-15
forum: Ubuntu Studio
---

### Post by michael_miceli on 2008-06-15
I have a Ubuntu server for my home, and I have a large amount of music stored on it.  I was wondering how I could create a stream from it so I would be able to access it from the internet?  I am new to this field and wondering.
Thanks
Michael

---

### Post by WeyOh on 2008-08-13
Hey Michael,

I have a similar situation. I have a home server on which I store my music. Currently I mount it as a folder (using nfs) and the client machines access it from there, but I also wanted to create a radio station that constantly plays a random music from my collection. Have you managed to create your internet radio? Anyone has suggestions?

Sam

---

### Post by finer recliner on 2008-08-13
check out jinzora

---

### Post by FakeOutdoorsman on 2008-08-14
Check out [ampache]("http://www.ampache.org/"):
> Ampache is a web-based audio file manager implemented with PHP and MySQL which allows viewing, editing, and playing audio files via the web. It has support for playlists, artist and album views, album art, random or vote-based play and per-user play-tracking/theming. Playback may be via HTTP, on-the-fly transcoding and downsampling, Mpd/Icecast, or integrated Flash player. Multiple Ampache servers can be linked together using XML-RPC. The software is fully localized in many languages.
It's in the repository.  I've never used it, so I can't give any experiences.  Also, MPD is very lightweight, but I don't know if it is used outside of local networks.  Clients for MPD include gmpc and sonata.  These are in the repo too.

---

