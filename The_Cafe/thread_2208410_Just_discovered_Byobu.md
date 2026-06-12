---
title: "Just discovered Byobu"
date: 2014-02-28
forum: The Cafe
---

### Post by ralph-beeby on 2014-02-28
Which is to say, I quite literally blundered across it yesterday on the dash, and investigated it because the icon looked pretty. Seems like a nice enough wrapper for the standard terminal, and I can see the tabbed sessions coming in handy for some of the stuff I'm doing just now. 

Of course, without trawling through the man pages, I don't know very much else about it! Any fans on here? I was just wondering if it had any nice little tricks or features I ought to know about.

---

### Post by ssam on 2014-02-28
Its very handy. Most of its ability comes from GNU screen (or tmux). Byobu is more like theme to make screen easier to use by default.

One very useful feature is that the session stays open even if you detach or get disconnected. So if you use ssh to run long processes on remote machines, you can run it in byobu (or plain screen), detach and then come back later and reconnect. Kind of like VNC for terminal.

---

