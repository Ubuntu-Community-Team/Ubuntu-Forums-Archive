---
title: "xinetd, vnc, kdm - not playing nice"
date: 2006-12-27
forum: Server Platforms
---

### Post by TomalakBORG on 2006-12-27
Hey guys - running kubuntu 6.10 edgy,
Here's what I've been trying to do: (and my apologies to the admins if this post is in the wrong section - but I'm administering a headless server with vnc... so I thought it fit)

I want to connect to the current X server on ports 5900 (standard vnc) and 80 with the java http applet. I've gotten that to work by modding my xorg.conf for use with the vnc module. Cool, so I know vnc works.

Here's the other part of my adventures in vnc. I want to hit up port 5901 and start a new session, complete with kdm login screen. 

Here's what I'm working with:
[http://ubuntuforums.org/archive/index.php/t-259448.html](http://ubuntuforums.org/archive/index.php/t-259448.html)
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)
[http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions](http://gentoo-wiki.com/HOWTO_Use_VNC_to_connect_to_existing_X_Sessions)

Here's what I've done-
[LIST]
[*] Installed xinetd - I have Xvnc and xvnc4 installed as well
[*] Created /etc/xinetd.d/vnc
```
service vnc-1024x768x16
{
        socket_type = stream
        protocol = tcp
        wait = yes
        user = root
        server = /usr/bin/Xvnc
        server_args = :1 -inetd -query localhost -once -geometry 1024x768 -depth 16 -SecurityTypes=None
}
```
[*] Added the following to /etc/services
```
# VNC Services
vnc-1024x768x16 5901/tcp
```
[*] Created /usr/adm with read/write permissions so xinetd could dump a log
[/LIST]

Here's what's happened:
I cannot connect - I get a "connection reset by peer" error. Let's check the log in /usr/adm:
```

Wed Dec 27 15:46:37 2006
 vncext:      VNC extension running!
 vncext:      inetd wait
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/X11/fonts/misc/, removing from list!
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/Type1/, removing from list
!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
Could not init font path element /usr/share/X11/fonts/100dpi/, removing from lis
t!
Could not init font path element /usr/share/X11/fonts/75dpi/, removing from list
!

Fatal server error:
could not open default font 'fixed'

```
Hmmm.... well my xorg.conf does list those locations in the "files" section... are they wrong? On a hunch I found the fonts myself, and they reside in **/etc/X11/fonts/X11R7/**, not **/usr/share/X11/fonts/**

After changing my font paths in xorg.conf (which works either way - should that be so?) I get the same error. 

Any ideas? Thanks in advance!
Bill

---

