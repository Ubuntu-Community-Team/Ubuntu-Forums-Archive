---
title: "Setting up a linux fileserver?"
date: 2010-03-21
forum: Server Platforms
---

### Post by Mr.SASQUATCH on 2010-03-21
hi guys, I've been using ubuntu desktop now for about a month and I'm loving it so far and have been thinking about what I could do next with it. For the past 6 months or so I've been using a spare PC running windows as my fileserver for stream to my ps3 and to other computers around the house. 

I'm wanting to get rid of windows and move to ubuntu on the fileserver but not sure how exactly to set it all up. I'm wanting to take things a bit further with the the new isntall and was thinking in addition to the fileserver I would set it up as a firewall and squid/proxy. 

I'm looking for suggestions and tips on what the best packages to install and how exactly to install them and set them up. I know my way around ubuntu reasonably well, just not sure on where to start or look for in regards to setting up what I mentioned above. 

I take it that I would be best off installing ubuntu server and setting up something like samba for the fileserver?

I'll be running the following services:

- Samba - for file storage/sharing
- SoftRaid RAID 5

---

### Post by jrssystemsnet on 2010-03-21
You need Samba for sharing with PCs.  **sudo task-sel install samba-server**.  There are plenty of guides for basic Samba configuration.

You'll need a UPnP server for streaming to your PS3.  Mediatomb is one.  I'm not too sure which is currently the best one for the job; but that's the actual thing that you need - a UPnP (Universal PlugnPlay) server.

---

### Post by Iowan on 2010-03-21
This [Server Guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html")  touches on several different servers. It might be a good place to review some of your options.

---

