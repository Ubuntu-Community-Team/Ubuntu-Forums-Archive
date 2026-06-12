---
title: "Plex client on ubuntu server"
date: 2020-01-05
forum: Server Platforms
---

### Post by kulmanrenato on 2020-01-05
Hi!
I have a ubuntu server running Ubuntu 18.04.3 LTS. There is a plex server running on it, but i would like to use it as a client with plex or kodi. Is it possible to do it without installing a full desktop enviroment or maybe a command that turns off the gui to save power when i dont use it?

---

### Post by Tadaen_Sylvermane on 2020-01-05
In the past my main server was also my living room htpc via Kodi, direct boot to it. It can be done fairly easily and you don't need a full DE to do it. I'd recommend Openbox and a systemd service to autostart Openbox on the proper user. Then in the Openbox autostart you have your Kodi start script. I'm assuming this would also work for a Plex client, I have never used Plex so I cannot be certain. Once it's working just point Kodi ( or plex?) at your nfs share or your server like normal and it will work fine. As far as stopping the gui? The power draw is absolutely minimal when it's idling. Not even worth trying to work out. I left my Kodi up 24/7. I just turned off the TV.

---

### Post by kulmanrenato on 2020-01-05
> **Tadaen_Sylvermane said:**
> In the past my main server was also my living room htpc via Kodi, direct boot to it. It can be done fairly easily and you don't need a full DE to do it. I'd recommend Openbox and a systemd service to autostart Openbox on the proper user. Then in the Openbox autostart you have your Kodi start script. I'm assuming this would also work for a Plex client, I have never used Plex so I cannot be certain. Once it's working just point Kodi ( or plex?) at your nfs share or your server like normal and it will work fine. As far as stopping the gui? The power draw is absolutely minimal when it's idling. Not even worth trying to work out. I left my Kodi up 24/7. I just turned off the TV.

Wonderful, it looks easy.
i guess i will go with kodi since plex is not fully supported as i know, i will check it out when i have some free time for that.
Thank you very much :)

---

### Post by howefield on 2020-01-05
Thread moved to the "*Server Platforms*" forum.

---

