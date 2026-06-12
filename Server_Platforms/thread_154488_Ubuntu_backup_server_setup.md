---
title: "Ubuntu backup server setup?"
date: 2006-04-03
forum: Server Platforms
---

### Post by Stealth on 2006-04-03
Hey guys, I have this lil old machine here running as a server for different things. Its my FTP server, Soldat (a game) server, and also has SSH for whenever I may need to access it remotely. BUT I'd like to have it as an automated backup server too. I already copy-pasted my main files there, but I'm wondering how I can go about doing this automatically? Something like, have the server access a certain Samba share everyday, check which files are newer/aren't already backed up, and then copy those and throw em into a nice tar or something of all my files. Anyone have any suggestions for programs and methods to go about doing this?

---

### Post by skirkpatrick on 2006-04-03
Somebody mentioned SimpleBackup (Synaptic = sbackup) running on the client-side (Ubuntu) that you can manually backup or schedule including to a Samba mount.

---

