---
title: "X-Forwarding virtual display"
date: 2013-12-21
forum: Server Platforms
---

### Post by Crypdos on 2013-12-21
Hello,

I have a headless ubuntu 12.04 server which I want to use to download steam games at night. I got it working, but the whole thing is very unstable and so far I have not managed to succesfully download a game before it crashes.

Right now I do this:

- Installed steam using the latest Wine (to download the Windows version of the games, I can't use the native linux-steam for this I believe)
- Use xpra to run steam in a "screen"-type display, I attach to this display via X-forwarding with putty and Xming under Windows
- Transfer the game files via Samba over the network. Didn't get this far though, too unstable.

I really like the functionality of this setup, I can attach and detach to this screen easily. However, it's very unstable.

So, I wonder if there is a better way to accomplish my goal. I read about Xvfb and how it runs X programs in the virtual memory, instead of outputting them in a display. (correct me if I'm wrong)
Is Xvfb what I need? Would it improve stability or decrease server load? I could still display these X programs with VNC or X-forwarding right? 

Every idea is welcome! :)

---

