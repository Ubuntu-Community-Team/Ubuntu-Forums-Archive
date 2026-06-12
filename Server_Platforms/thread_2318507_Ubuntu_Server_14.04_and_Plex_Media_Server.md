---
title: "Ubuntu Server 14.04 and Plex Media Server"
date: 2016-03-26
forum: Server Platforms
---

### Post by rdutchak on 2016-03-26
I'm not getting any traction on the Plex forums, so maybe this is something for the Ubuntu forums.

This is copied directly from the Plex Forum:

I'm not sure if this is a Plex issue or a Linux (Ubuntu 14.04.4 LTS) issue, so I figure I'll ask here first.

Often, we'll set up the Plex (playing through Xbox360) to play a big queue of kid shows for my daughter, which typically becomes background noise for her, and after it plays about six episodes back to back (about 20 minutes long each), it freezes, I can't ping it, and I can't get a response from the display direct connected. I'm forced to power it off and back on to get it back online.

Has anyone else had this issue, is there a way to fix this?

---

### Post by Thirtysixway on 2016-04-23
If it's easy to recreate, you could run something like top or htop on the server while streaming. It sounds like it could be running out of memory. I am not super familiar with Plex however I do know it needs to load videos into memory & do some encoding and other processing to get it over to the xbox.

---

### Post by Magneto on 2016-04-24
Yup sounds like memory issue or the cache filling up and the app crashing the entire system. Run Plex in verbose/debug mode and go through your 6 show motion and check the log it creates for what went wrong. Most likely it has happened to others and there is a fix in the Plex community.

How to turn on Debug mode in Plex
[https://support.plex.tv/hc/en-us/articles/201643703-Reporting-issues-with-Plex-Media-Server](https://support.plex.tv/hc/en-us/articles/201643703-Reporting-issues-with-Plex-Media-Server)

Plex Log Info
[https://support.plex.tv/hc/en-us/articles/200250417-Plex-Media-Server-Log-Files](https://support.plex.tv/hc/en-us/articles/200250417-Plex-Media-Server-Log-Files)


What are your Plex server specs?

---

