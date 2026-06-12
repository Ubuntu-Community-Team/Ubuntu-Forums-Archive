---
title: "Best media player for smb"
date: 2009-04-25
forum: The Cafe
---

### Post by Eviltechie on 2009-04-25
I've got all of my music on my nas. What is the best music player to play it? I want it all in a library, but not locally on my computer.

---

### Post by yabbadabbadont on 2009-04-25
You can setup mpd on the local machine (and use whichever front end you like).  Then just create symbolic links in mpd's music directory that points to the mount point directory that you use to access your NAS.

I do something similar on my Gentoo machine.  All my music is located under /mnt/music and the mpd music directory is /var/lib/mpd/music so I just created links there.

```
/var/lib/mpd/music $ ls -l
total 0
lrwxrwxrwx 1 root root 15 2009-04-21 00:03 Flac -> /mnt/music/Flac
lrwxrwxrwx 1 root root 14 2009-04-21 00:03 MOD -> /mnt/music/MOD
lrwxrwxrwx 1 root root 14 2009-04-21 00:03 MP3 -> /mnt/music/MP3

```

mpd on Ubuntu may use a directory other than /var/lib/mpd/music, but this general idea should work.

---

