---
title: "How to download torrents outside of the user's directory with rutorrent"
date: 2017-06-24
forum: Server Platforms
---

### Post by ltzerouk on 2017-06-24
Hi,
I have set up a server with Ubuntu 16.04 and installed the Quickbox package on it with Plex. My idea is to have multiple accounts, one for me, one for my brother and posibly one for a friend. For the downloads that aren't films and series, I want to keep them separated in the respective user directory. Until here every thing works. 
Now I want rutorrent to be able to also download files do a shared directory located in the /home/ directory where all the films and series will be downloaded by the different users to be shared through Plex so we don't three times the same film but it dosen't want to do it. Same problem as soon as I try to locate the download directory outside of the user's directory in general. I tried to give general access to the directory with ```
chmod -R 777
``` but it didn't work. I also tried to make a group shared directory but this didn't worked either.
Any help would be welcome

---

### Post by howefield on 2017-06-24
Thread moved to the "*Server Platforms*" forum.

---

### Post by ltzerouk on 2017-06-25
Sorry if I posted in the wrong thread. I wasn't sure in witch it belonged. I finally don't require your help anymore. I found another way to solve my problem. I gave access to Plex to the other user's folders and it seems to work fine.

---

### Post by howefield on 2017-06-25
Cool, well done on finding a solution and thanks for marking the thread as solved.

---

