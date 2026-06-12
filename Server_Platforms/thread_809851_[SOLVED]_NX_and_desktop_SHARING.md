---
title: "[SOLVED] NX and desktop SHARING"
date: 2008-05-27
forum: Server Platforms
---

### Post by nowhere@cox.net on 2008-05-27
Hey everyone,

I just downloaded and installed nomachine's free nxserver/node/client package on my server box at home and client on my laptop using Sprint EVDO. Took all of 4 minutes to be up and running on both and I connect flawlessly. 

I did notice however that a seperate x session or something is loaded when I use the nxclient to log into my server (and by server I mean a Ubuntu Desktop box running at home). I had VNC open along with nx and VNC affected my desktop on the monitor at home while nxclient did not. 

Is there a way to use nxclient to connect to the desktop someone is using? I am looking at this because I have just convinced my wife to go Ubuntu and I anticipate having to share her desktop from time to time to teach her things I have learned since I am a bit ahead of her in the learning.

I am impressed with the speed and stability of connection of the nx system tho...

Thanks!

---

### Post by nowhere@cox.net on 2008-06-05
I think I've figured this out. NX rocks! Only problem I have is that I would like to be able to choose whether to shadow the current desktop or start a new session. I CAN do this but it requires editing the saved profile every time I want to switch back and forth. Anyway. Kinda solved since I am starting to get the hang of it.

---

### Post by Lisanels on 2008-06-30
I use multiple profiles instead of editing them.  For example, I have 
Remote-Lisa-console
Remote-Lisa-Shadow
Remote-Lisa

This works great, and I use no-ip to setup a constant name on the internet.  It's free too.

My only issue is that with the new fedora 9, shadow sessions show as user root instead of who they really are.  I'm trying to figure that one out now...  The fedora 8 system shows the correct user when I shadow to it.

Lisa

---

### Post by wdephillips on 2009-09-03
Would you mind sharing how you got it to work?  I'm trying to accomplish the same thing so I can leave my gnome session running at work and connect to it from home.

---

### Post by wdephillips on 2009-09-09
I was just looking in the wrong place.  I thought Shadowing was an option of the specific session but it is actually a entirely new type of session, like GNOME, VNC, etc.  It is available in the Desktop dropdown that also lists Windows, Unix, VNC, and Shadow.

---

