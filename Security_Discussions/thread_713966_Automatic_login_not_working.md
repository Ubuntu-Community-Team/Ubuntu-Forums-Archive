---
title: "Automatic login not working"
date: 2008-03-03
forum: Security Discussions
---

### Post by nloding on 2008-03-03
I've done some searching and didn't find the answer to this anywhere.  I have automatic login enabled (not timed, just go straight in), and it works great -- when I have a monitor and/or keyboard attached to it.

It's my in-house webserver, no access externally, so security isn't a concern.  I want it to boot normally with just power and a network cable attached.

I plug it into my workbench setup, monitor, kb, mouse, and everything; it boots just fine -- it logs me in automatically to GDM so I can VNC into my active desktop session, SSH into it, use Samba, etc.  So I shut it down properly, disconnect, hook it to the power and network cable in my server closet (literally a closet :) ) and power it back on.

I can SSH into it, use Samba, but VNC fails.  I can only assume it's not automatically logging me into an active session.  But if I pull it out and hook a monitor and keyboard to it, it works fine.

Is there a security setting somewhere that prevents automatic login without a keyboard/mouse/monitor attached?

---

### Post by nloding on 2008-03-04
I found a reference to this not being possible headless, but that seems dumb.  Why wouldn't a graphical session start if a monitor isn't detected?

I'm having terrible trouble trying to configure tightvncserver or x11vnc for resumable sessions (the tutorials on this site don't work, and all the Gutsy tutorials I've found don't work either, so I must be doing something wrong).  I was just hoping that since security isn't a concern, I could get it to the auto-login and then I could VNC in from there ... grrr ...

No one has any thoughts?

---

