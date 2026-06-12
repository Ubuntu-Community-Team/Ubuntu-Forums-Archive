---
title: "how do i  move to desktop ubuntu?"
date: 2009-11-15
forum: Server Platforms
---

### Post by gobbledigook on 2009-11-15
Hi!

i am seriously considering moving over to the desktop ubuntu as i have had no end of issues with the sound on the server platform... i know its not "supposed" to have sound, being a server  an all but i have been using it as a media centre. My sound issues are chronicled [**_here_**]("http://ubuntuforums.org/showthread.php?t=1292977") however i have had no response to my post on the xbmc forums either - I have used the sound issues troubleshooting thread over in the multimedia section of the ubuntu forums but my problem is that it works but is very quiet... to the point where i need to have the amp on MAX to watch something :( this is the same on all playback software i have tried: xbmc vlc totem etc... 

I have a server box at the moment which i use for:
- file storage
- samba share on my LAN 
- host a few web pages
- record a web-stream with a scheduled cron job
- has ftp server
- use utorrent via webgui + wine + vnc
- use sabnzbd
- also use XBMC as a media centre to show video etc on the telly downstairs - via s-vid cable 

i currently have a basic fluxbox desktop environment which is all i thought i needed. But the sound has become such a bit issue that now i am wanting advice on the best way to migrate myself over to the desktop ubuntu :(

any help greatly appreciate!

Dan,

---

### Post by shred_eng on 2009-11-15
uninstall alsa and pulse and try oss4, it works for me, :)

---

### Post by gobbledigook on 2009-11-16
> **shred_eng said:**
> uninstall alsa and pulse and try oss4, it works for me, :)

hey! this has worked a treat! i looked at it before but xbmc needs alsa for audio so i dismissed it. However on the ubuntu how-to for installation of oss4 it points to where you can emulate alsa if needed... set this up, and now i can hear stuff at a decent volume :)

thanx for your reply! now i have no need to get rid of my server set up :popcorn:

---

