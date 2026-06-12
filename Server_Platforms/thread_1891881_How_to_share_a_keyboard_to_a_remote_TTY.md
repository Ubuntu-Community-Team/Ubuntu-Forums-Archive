---
title: "How to share a keyboard to a remote TTY"
date: 2011-12-06
forum: Server Platforms
---

### Post by isaacdl on 2011-12-06
I have a computer running Ubuntu as my primary machine. It has an external keyboard hooked up to it.

I'm also setting up an older laptop as a server. I have it set up in such a way that I can see and use the screen on it, but the keyboard and mouse aren't really reachable. It has Ubuntu Server on it, obviously without a GUI.

I'm looking for some way that I can use the keyboard hooked up to my primary machine to administrate the server laptop, while still using that laptop's screen (i.e. not SSH). I'm looking for something like Synergy, but not dependent on an X-server.  

I would like it to be easy to switch, maybe a hotkey or even just moving the mouse off the edge screen on the primary computer, a la Synergy.

Any ideas?

---

### Post by volkswagner on 2011-12-06
Sounds like an inexpensive USB keyboard is in your future.  Syngergy is the most likely tool, but it certainly would require the installation of Xserver.

It just seems like a specifically odd request.  Most folks are happy to have a server with no keyboard and no monitor.  It is difficult to grasp why you care to utilize the screen.  None the less I think you have done your research.  I'd be very surprised if you can find a solution that is not hardware based.

---

### Post by isaacdl on 2011-12-06
I want to do this so that I don't take up any screen real estate on my primary machine. This is going to be a development and testing server for trying some new projects, so I anticipate needing to interact with it a fair about.

I don't have room on my desk for another keyboard. 

If I can't find anything else I'll probably have to install a GUI and use Synergy.

---

### Post by volkswagner on 2011-12-07
If desk space is the issue, I'd suggest ditching the server screen and adding a second monitor to your work station.  This would allow you to dedicate the second monitor to your ssh session.

---

