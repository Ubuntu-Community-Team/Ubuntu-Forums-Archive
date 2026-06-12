---
title: "DLNA Server Suggestions please"
date: 2010-05-26
forum: Server Platforms
---

### Post by spynappels on 2010-05-26
Hi people,

I am now finally getting rid of my Windows 2003 server and transferring everything over to a Linux server, and I want to consolidate the various other Linux servers that I have been running as testbeds etc into 2 Ubuntu servers.

I will run one as a VPN Server and Web Server with other bits and pieces as required, and the other as a SMB File server and DLNA server. HArdware spec is fine for both boxes, but I am looking for recommendations for a DLNA server. I have played with miniDLNA and found it quite good, but I'd like to know what other alternatives are being used and why they are good, bad or indifferent. I'd prefer to have a Web frontend if possible, and the option of streaming to iTunes and support for streaming Video, Audio and images at fairly high bitrates to HD Media Players.

All suggestions gratefully accepted.....

---

### Post by arrrghhh on 2010-05-26
Hrm, I've always streamed to set-top boxes like the PS3.  I use ps3mediaserver, I've never used it with anything but a PS3 - but it works fantastically for that.  Not sure how well it works with other devices, never tried...

There's also mediatomb, it was good - but kinda difficult to setup, and didn't work nearly as well as ps3mediaserver.  I have a repo for it if you want to try out the newest, as it's not in the ubuntu repo's.

There's others - ushare, twonky come to mind... Just never used them personally.

---

### Post by spynappels on 2010-05-26
Hi and thanks for the reply.

I will be streaming to WDTV Live players as well as various laptops running WMP and similar and an old XBox running XBMC.

Files are mostly DVD Rips in MKV format which the XBox struggles with, and some older AVIs

I may look at Twonky, but would prefer to look at free offerings first. Simpler would be better, but I'll have a look at MediaTomb.

Keep the comments coming!

---

### Post by arrrghhh on 2010-05-27
Definitely give PS3MediaServer a shot.  I know that it's geared towards the PS3, but I've also heard that the PS3 is one of the better implementations of a standards-compliant DLNA client - so the PS3MediaServer actually does work with a lot of other devices, I've heard quite well.

Mediatomb was nice, but a PITA to setup and I could never get it to transcode properly.  PS3MediaServer, no problems whatsoever.  I've only used it on my PS3 and my TV (which also does UPnP streaming) and it works flawlessly with the PS3.  The TV... not so much, but as I understand it that device isn't so standards compliant :P  I should try connecting it to my Win boxes, I never have...

---

