---
title: "Bittorrent to mirror the repository?"
date: 2005-10-18
forum: Repositories &amp; Backports
---

### Post by jek on 2005-10-18
The use of debmirror puts a fair load on one host.

Would it be possible and/or make sense to provide seeds for bittorrent for the various repositories to implement the replication?

---

### Post by kakashi on 2005-10-29
[QUOTE=jek]The use of debmirror puts a fair load on one host.

Would it be possible and/or make sense to provide seeds for bittorrent for the various repositories to implement the replication?[/QUOTE]


i am currently in the process ofcopying all the files in ubuntu mirror for i386
(universe multiverse restricted and main) 
i will soon make a torrent of this if you want and you can dl that.

---

### Post by djlosch on 2005-10-31
i was just figuring, why not make it so everyone who doesnt mind participating automatically uploads via bittorrent.  i know i wouldnt mind lettin people dl from me from like 9am-5pm and 1am-6am.

when i dl'd the ubuntu dvd it got up to like 1.2 mbps.  i've never dl'd something that fast off the internet.

---

### Post by the_clown on 2005-11-01
Someone already did this for debian: [APT-TORRENT]("http://sianka.free.fr/documentation.html")

---

### Post by xequence on 2005-11-01
I had thought of this idea along time ago but didnt post it. Its similar to yours...

Make a hybrid repository. The repo servers and bittorent seeds work together. If there are alot of seeds to get a fast speed, no server is needed but if there are only a couple seeds then the server does a bit more work.

It would never slow anything else down, as in it would autodetect the other stuff you are downloading and not keep any bandwidth from them, it would just use the free bandwidth.

Then it could run as a daemon in the background until the person gets to 120% (though the person could opt out if the wanted).

If not that it could just help distribute while in the process of downloading then stop when the download is done.

[QUOTE=the_clown]Someone already did this for debian: [APT-TORRENT]("http://sianka.free.fr/documentation.html")[/QUOTE]

Debian repos cant be used with ubuntu.

---

### Post by Pettman on 2005-11-02
[QUOTE=djlosch]i was just figuring, why not make it so everyone who doesnt mind participating automatically uploads via bittorrent.  i know i wouldnt mind lettin people dl from me from like 9am-5pm and 1am-6am.[/QUOTE]I agree with you, I would not mind sharing my abundant bandwith with the rest of the ubuntu comunity.

---

