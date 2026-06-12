---
title: "Kodi Media Center issue"
date: 2015-04-27
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2015-04-27
Topic makes it sound like its not a server. Main installation is Ubuntu server 14.04.2. I have set it up to direct boot to Kodi (formerly XBMC) and do my "server" stuff over ssh with putty. It is currently a file server / media server / minecraft server / torrent server & apt-cache proxy. I leave this box running at all times to fill it's role as a server. Not a problem, it's always on. I just finished setting this up the other day and its been working great as an htpc + the other tasks.

The problem...

This morning I went to the living room, turned on the tv and switched it to the HDMI channel for the server. It kept saying no signal. The Kore app on my phone (the kodi remote control over network) kept trying but couldn't connect at all. I went to my laptop and ssh into the server with no trouble, a pgrep -u xbmc -f kodi showed that it was running just fine. My guess is that at some point, possibly because it didn't detect a monitor / screen available it went into standby kind of? Rebooting the machine and it's all working great. The Kodi power saving options are all disabled in the gui so I'm assuming it's something with the server installation.

How can I find what cause this issue? And further can I write a script or something to run in cron maybe every half hour or so to keep it from doing whatever it did to cause the problem?

The end result I'm looking for is that whenever you switch to the HDMI channel Kodi should be there waiting for you.

---

### Post by TheFu on 2015-04-27
Try disabling the monitor sleep mode.
```

xset +dpms &
xset s on &
```

This will need to be run AFTER X/Windows has started and for the userid running Kodi. Don't recall where I did this on my Kodi box.  BTW - mine does what yours does minus the torrent stuff, +NFS server for the network and as the household Plex Server too.

---

