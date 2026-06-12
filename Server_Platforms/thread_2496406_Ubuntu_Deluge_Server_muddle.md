---
title: "Ubuntu Deluge Server muddle"
date: 2024-03-26
forum: Server Platforms
---

### Post by wobwill2 on 2024-03-26
Hi Ubuntu Forum!

This is a the same issue as posted at the deluge support forum here: [https://forum.deluge-torrent.org/viewtopic.php?t=56761](https://forum.deluge-torrent.org/viewtopic.php?t=56761)

I am posting here as well as this may be an ubuntu rather than deluge issue? 

I cannot access /var/lib/deluged despite adding USER to both DELUGED and DELUGE-WEB groups and making sure those groups have rwx access to the folder. 

I now cannot start the deluge service or the deluge-web service, as per the other post. As in that post please can anyone advise me:

1. how to reset deluge and deluge-web so that they start?
2. how I can access /var/lib/deluged so that I can move the files I have downloaded

thank you!

---

### Post by wobwill2 on 2024-03-26
[PARTIAL SOLVE]

I realised that I had failed to add the -R flag when adding user to groups. In the end I changed ownership of the folder to user with the -R flag and was able to move the files I needed. I will now purge deluge and deluge-web and no doubt start again.

---

