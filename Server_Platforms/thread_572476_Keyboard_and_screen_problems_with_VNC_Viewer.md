---
title: "Keyboard and screen problems with VNC Viewer"
date: 2007-10-10
forum: Server Platforms
---

### Post by piercleo on 2007-10-10
Hello all,

I am using VNC over SSH and I have two little problems:

Screen problem:

When i type in the command:

vncviewer -via ipadress cpuname:0

I have access to my remote desktop but the screen resolution is awfull. The remote desktop I access has a 1440x900 resolution wheras the laptop from which I am accessing the remote desktop has a 1024x768 resolution. Hence I see only part of the remote desktop screen.

Keyboard problem:

If I access the remote desktop through the following command:

vncviewer -fullscreen -via ipadress cpuname:0

Than the keyboard doesn't work at all !

Any help would be greatly appreciated since i've been searching this problem for quite some time now.

best regards,

Piercleo

---

### Post by James79 on 2007-10-10
> **piercleo said:**
> 
I have access to my remote desktop but the screen resolution is awfull. The remote desktop I access has a 1440x900 resolution wheras the laptop from which I am accessing the remote desktop has a 1024x768 resolution. Hence I see only part of the remote desktop screen.


Have you tried experimenting with the "-geometry" parameter for vncviewer/vncserver?

The vnc viewer I have (for windows) allows me to *scale* down the image. This isn't quite the same as resizing, as the image is only resized on the client side as if it were a picture. But it did work well enough for me.

---

### Post by piercleo on 2007-10-11
No i didn't. I looked in the vncviewer manual and it doesn't say how to use the -geometry command. In my case it would be:

vncviewer -geometry 1024x768 -via ipadress

Is that correct ?

piercleo

---

### Post by James79 on 2007-10-11
Yes I believe so. Try with something smaller maybe, 800x600.

Like I said, my windows vncviewer allowed me to scale the image after I was connected. Maybe look for a similar option in the menus.

Sorry I can't be of more help, I don't have access to a linux vncviewer at the moment.

---

### Post by pageauc on 2007-10-14
I also had a problem with scroll bars accessing my windows xp machine from ubuntu fiesty machine.  xp has higher resolution than ubuntu machine.  I discovered that the mouse left click on the scroll bar moves to the vnc view to maximum down or right depending on the scroll bar you pick.  By trial and error I found the mouse right button moves the appropriate scroll bar up or left in increments.  You may want to try this.  At least I can navigate my XP desktop in the VNC window.

---

