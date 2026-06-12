---
title: "viruses in bittorrents: a concern?"
date: 2008-10-03
forum: Security
---

### Post by dgo.g on 2008-10-03
Dear all,

I recently learned that wine uTorrent.exe works charmingly 
so that one can download bittorrents without problems under linux.

I use the above to download music / films, that I play
with, say, amarok or kaffeine, respectively.

I was wondering whether there may be any security issue,
about viruses or trojans. I know that under linux the risk 
is very low, but still:

1) Should I scan downloaded files (99% are *.mp3 *.avi) with antiviruses like AVG-Free? 
2) Is there any risk that malware somehow attached to, say, music files can make any harm when I just play those files?
(players do not escalate privileges, do they?)

Thanks a lot!
D

---

### Post by lisati on 2008-10-03
There's no harm in scanning the file(s), even though the occasional occurence of malware is unlikely to hurt your Ubuntu system. You might, however, want to make sure that Wine doesn't have access to your "/" directory through the "Z" drive (I don't currently have wine installed, so I'm not in a position to remind myself where to find the place to check that option)

---

### Post by kingpoiuy on 2008-10-03
There are plenty of torrent programs for Linux.  Some are available in the add/remove section in Ubuntu.  I don't see any reason to use WINE for this unless you just really like utorrent.

---

### Post by iponeverything on 2008-10-03
Short answer: no.

There has been proof of concept viruses that have gotten a lot of press, but nothing in the wild that has ever gotten a foothold.  That, I am aware of.

Worms and script kiddies are another case altogether, mis-configured and neglected Linux boxes are big problem.  That is why it good to turn off services you don't need, and limit access to those that you do.

ref: [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Don't let any huckster try to trick you thinking that you need virus software for Linux machine, unless its to scan mail bound for windows machines.

---

### Post by hyper_ch on 2008-10-03
why not using a linux nativ torrent client? Chance that you encounter a virus written for linux is close to 0 and even if you do, by opening a file in a media player (kaffeine, vlc) will have no effect on your system - except if that file targets a weakness in that player.

---

### Post by bodhi.zazen on 2008-10-03
> **dgo.g said:**
> Dear all,

I recently learned that wine uTorrent.exe works charmingly 
so that one can download bittorrents without problems under linux.

I use the above to download music / films, that I play
with, say, amarok or kaffeine, respectively.

I was wondering whether there may be any security issue,
about viruses or trojans. I know that under linux the risk 
is very low, but still:

1) Should I scan downloaded files (99% are *.mp3 *.avi) with antiviruses like AVG-Free? 
2) Is there any risk that malware somehow attached to, say, music files can make any harm when I just play those files?
(players do not escalate privileges, do they?)

Thanks a lot!
D

Torrent is nothing more then an internet protocol for file sharing. As with any download, you should trust the source before you install the code.

---

### Post by stormtrooprdave on 2008-10-04
Use Transmission instead

---

### Post by Dave_Connor on 2008-10-04
If you want UTorrent that runs without WINE there is Deluge which is alot like UTorrent with its interface and functions. Plus it is really awesome client.

---

