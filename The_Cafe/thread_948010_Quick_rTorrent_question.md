---
title: "Quick rTorrent question"
date: 2008-10-14
forum: The Cafe
---

### Post by Dr Small on 2008-10-14
I am trying rTorrent for the second time (and yes, I've read K.Mandla's rTorrent post). But I have a quick question.

When I start download my 700MB torrent, it created the file and automatically it's size is 700MBs. I know it hasn't downloaded that much that fast, so I am asking, is that the normal behavior of rTorrent?

---

### Post by zekopeko on 2008-10-14
/me thinks that's ok.

[http://en.wikipedia.org/wiki/Sparse_file](http://en.wikipedia.org/wiki/Sparse_file)

---

### Post by Dr Small on 2008-10-14
Ok, thanks. That explains that. One more question:
How can I disable upload completely? My connection can't handle it much, and I have restrictions.

---

### Post by yabbadabbadont on 2008-10-14
You can set the upload bandwidth to 0kb/s and/or the number of simultaneous uploads to 0.  However, your torrents will take forever to complete, if ever, if you do that.

---

### Post by graabein on 2008-10-15
I have a quick one as well (while he's away) [link]("http://www.youtube.com/watch?v=bCKlr5qeiQY"); how do I continue downloading a torrent from a previous session? See I logged on and started a download with rtorrent. Then I had to shutdown the machine. When I log back on I'd like rtorrent to continue where it left off...

---

### Post by Dr Small on 2008-10-15
> **graabein said:**
> I have a quick one as well (while he's away) [link]("http://www.youtube.com/watch?v=bCKlr5qeiQY"); how do I continue downloading a torrent from a previous session? See I logged on and started a download with rtorrent. Then I had to shutdown the machine. When I log back on I'd like rtorrent to continue where it left off...
Just open the torrent back up, and start it again. It should start up where it left off.

---

### Post by bobbocanfly on 2008-10-15
> **Dr Small said:**
> Just open the torrent back up, and start it again. It should start up where it left off.

Yep, whenevr you start a torrent in most clients nowadays they do a hash check to see what has been downloaded, then continue just as you left off. 

And yes, it is normal behaviour or most torrent clients to allocate all space for a torrent in one go. I can think of several good reasons why the would do this (lets you know if you have enough space to complete the download instantly, probably some disk optimization (though that is a guess).

---

### Post by simtaalo on 2008-10-15
yup is standard behaviour for torrent clients.

---

