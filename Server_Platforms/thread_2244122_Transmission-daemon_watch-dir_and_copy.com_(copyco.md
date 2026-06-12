---
title: "Transmission-daemon watch-dir and copy.com (copyconsole), permissions problem"
date: 2014-09-13
forum: Server Platforms
---

### Post by kokotron2 on 2014-09-13
Hello there,

I have setup transmission to use as a watch-dir a local folder that syncs from copy.com (via copyconsole, works fine). It seems that transmission doesn't like the default permissions of the torrent file. Any new file added in copy.com and synced will have a (reasonable) permission of 700 (-rwx------). Nothing happens, UNLESS I chmod the torrent file to 775 (-rwxrwxr-x) and restart the transmission daemon, then the torrent will load. How can I control this? Would it be easier to make copyconsole sync every file as 775 or would I rather make transmission read files with 700 permission? How do I go doing any of that?

Cheers

---

### Post by kokotron2 on 2014-09-14
Found the solution, refer here: [https://forum.transmissionbt.com/viewtopic.php?f=2&t=16431](https://forum.transmissionbt.com/viewtopic.php?f=2&t=16431)

---

