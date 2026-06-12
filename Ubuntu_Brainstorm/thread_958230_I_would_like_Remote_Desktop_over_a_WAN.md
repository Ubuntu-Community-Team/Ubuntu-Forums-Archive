---
title: "I would like Remote Desktop over a WAN"
date: 2008-10-25
forum: Ubuntu Brainstorm
---

### Post by bwallum on 2008-10-25
Hi

Having come off Windows now, I have been spreading the word and now have 5 Unbuntu users converted from Windows. Every so often they will call and ask how to do such and such. I would like to access their machine and see what needs to be done, with the convert visually tracking what I am doing. 

The scenario would run something like this:-

Remote party sends email with full path details (their ip address, machine name and port number)
I would connect to their machine by clicking on the link they sent to me.
They would accept the connection and away we go with doing whatever needed to be done.

I have managed to use vinagre over a LAN. I would like to be able to do this over a WAN, i.e. over the Internet and using SSH for a secure tunnel.

---

### Post by thefrozenpenguin on 2008-11-15
hi bwallum, I have a similar situ and would like to use vingre over the WAN to my elderly uncle who now has a Intrepid box, have you had any responses or further info as to how to do this?

---

### Post by bwallum on 2008-11-16
Hi, sorry about the delay in responding. Basically I have not moved forward that much although have read a lot! It seems to be that it can be done, however is a little insecure and that work is ongoing. I guess that has left me demotivated to put it high up my priority list. I do still dabble with it and have a running note (attached) which is my memo to myself when I pick it up from time to time. My main block at present is the syntax of the command used in vinagre to achieve communications through to the target router.

I'll keep you posted should I make the breakthrough. Let me know if you have any luck.

Regards
Bob

---

### Post by FokkerCharlie on 2008-11-18
+1 for interest in this subject!

I have a couple of relatives with whom a connection like this would be useful.  AND Mac users are boring me by telling me how they do it...

---

### Post by gnomeuser on 2008-11-18
openSUSE' [Nomad](http://en.opensuse.org/Nomad) project may provide a nice base for doing this kind of work. It currently does zeroconf autodiscovery on your local network as well as RDP. So it seems like a good place to start.

---

### Post by FokkerCharlie on 2008-11-19
OK, I think that I now have vnc working over LAN.  Here's the thread that helped me:

[http://ubuntuforums.org/showthread.php?t=986494]("http://ubuntuforums.org/showthread.php?t=986494")

Haven't been able to properly test it out, however.

---

### Post by smartboyathome on 2008-11-19
I would recommend FreeNX instead of VLC, due to how much faster it is vs VNC. Though FreeNX pretty much requires the proprietary client for now. :(

---

