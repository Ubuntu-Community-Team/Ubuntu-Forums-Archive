---
title: "Good server for streaming media and sharing files?"
date: 2014-07-15
forum: Server Platforms
---

### Post by Wiking on 2014-07-15
Any suggestions as to which type of server I should run to stream media (video, audio)? Also I will need the server to store files too ISO's, documents, and photo files.

It's for a home network but I would also like to access it remotely. I'm considering running a RAID 1 configuration. It would also have to allow Windows, Ubuntu, and Apple devices to connect.

---

### Post by rubylaser on 2014-07-15
I'd suggest [Plex Media Server]("https://plex.tv/downloads").  It's super easy to setup, and has Windows, Ubuntu, and IOS clients for streaming playback (even remotely if you port forward port 32400).  I would also setup a few Samba shares to share the folders you mentioned to your LAN.

---

### Post by TheFu on 2014-07-17
I agree with rubylaser's post. Plex Server is fairly easy and a great DLNA server - that means it will work with any DLNA client/renderer on the same subnet.  If you want access to these files remotely - know that the connections are NOT encrypted, so you many want to use a VPN to make that access possible.  There is NO requirement to get a Plex Account - just saying that now. Of course, I suspect having a Plex account would make non-local access easier.

I don't store ISOs on disk. That is extremely wasteful of storage (4x larger than necessary).

For ISOs and documents - that needs something other than plex.  There are at least 50 options and the level of security needed matters hugely.  CIFS shares are needed for Windows to access the files, but it isn't secure.  For UNIX-like OSes, NFS is the better choice. You can setup both for the same files/directories without worry.  I'd avoid NFS over the WAN or wifi. That is a personal decision and many people here don't have any issues using them over those less-than-great connection modes.

OpenVPN is probably the best solution for any remote access. Works from almost any platform.

RAID1 has nothing to do with the other decisions.  RAID comes AFTER you have backups working perfectly.  RAID can't solve anywhere near the problems that good backups solve since it only addresses HA. RAID never replaces the need for backups - NEVER!

---

### Post by cariboo on 2014-07-18
I use minidlna for streaming media, and Samba for sharing files on my 12.04.4 powered server. I use grsync to move files from my main system to the server. Anyone on my local subnet can access the media if the have a suitable dlna client.

---

### Post by cj13579 on 2014-07-21
I share my media from my server using NFS and SAMBA and stream media from it using XBMC (running Raspmc on Raspberry Pi) and also to my desktop using VLC over Samba. 

For getting access to my media outside of the house I use something that I wrote which is available on [GitHub]("https://github.com/cj13579/mediamonkey"). It's a PHP based media management system but it is tied in pretty close with XBMC (it uses its database for accessing media files).

---

