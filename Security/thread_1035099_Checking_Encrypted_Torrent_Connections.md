---
title: "Checking Encrypted Torrent Connections?"
date: 2009-01-09
forum: Security
---

### Post by flatline on 2009-01-09
Hi, I have a headless server at home running 8.04 x64.  It is connected to a nice, fat FIOS pipe (20/20) and is running the torrentflux webui.  I have been running moblock since day 1, but today I attempted to enable encryption as per this thread: _[http://ubuntuforums.org/showthread.php?t=724571](http://ubuntuforums.org/showthread.php?t=724571)_

My question is, how can I verify that my torrent client is now only running encrypted connections?  I have never run wireshark on a headless box, but I'm assuming maybe I could sniff the connection to check?  Thanks.

---

### Post by troutbum13 on 2009-01-09
ssh in from another machine and you could capture and examine packets, alternatively if you own the network you could arp poison and MITM your server and access point

---

### Post by HermanAB on 2009-01-10
Here is the trick:
If you use Wireshark or tcpdump remotely over SSH, tell it to ignore port 22, which is the one that SSH itself runs on!

Cheers,

Herman

---

### Post by hyper_ch on 2009-01-11
running rtorrent on a headless server and using encrypted connections only is easy to be achieved.

---

