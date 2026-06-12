---
title: "Best protocol / server for large file transfers?"
date: 2010-02-12
forum: Server Platforms
---

### Post by fowie on 2010-02-12
My server is doubling as a synchronization point for a couple of employees.  Currently, the only way I have set up for synchronizing (a very large number of custom .wav files) is for each client to FTP up their entire directory, possibly creating duplicates.  If the server ever reboots or the connection fails, it has to start all over again.  Is there no such thing as a recoverable FTP server/client?  What would be a better way to provide file synchronization?  Unison?  (None of the clients use linux, it's all Windows, and I'm lucky they can figure out how to use an FTP client).

---

### Post by smeerbartje on 2010-02-12
Well, since all users should be able to download the same folders, you can try to create at torrent fille. This also decreases the amount of bandwith the server needs.

Another way is secureftp; which has the ability to resume broken connections, but unfortunately is slower. Although I don't think you will notice this since the server's upload speed is the bottleneck.

---

### Post by drave on 2010-02-12
the linux way is rsync. there is a windows client (DeltaCopy) but ive never used it so cant really say how good it is

---

