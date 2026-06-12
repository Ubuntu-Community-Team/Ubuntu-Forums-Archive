---
title: "CLI instead of desktop at startup?"
date: 2008-08-10
forum: Server Platforms
---

### Post by G1ZmO65 on 2008-08-10
I installed the ubuntu desktop on my server a while ago and started xserver with startx (as far as I recall)

In an effort to reduce power consuption I wanted the GUI only to run when I told it to but it's running at startup each time.

How do I set it so that it just boots to the CLI when powered on?

Thanks

Paul

PS I'd also like to have the server suspend when not in use. How would I go about this? (shutdown will suffice if theres no other way but that would require manual startup)

PPS: the desktop seems to be locked at 640x480 which is a bit inconvenient. How do I change the res? (System/Preferences/Screen Res doesnt change it.) (No linux drivers for the onboard graphics on the motherboard)

---

### Post by pparks1 on 2008-08-10
I think that all you need to do is disable gdm from starting up at boot time.

System->Administration->services to disable gdm.

---

### Post by G1ZmO65 on 2008-08-10
Thanks, that disabled gdm :)

I'll start a fresh post for the other queries

Paul

---

