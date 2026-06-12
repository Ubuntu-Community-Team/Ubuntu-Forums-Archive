---
title: "vnc Doesn't Work Unless Monitor Is Connected"
date: 2011-02-17
forum: Server Platforms
---

### Post by roystreet on 2011-02-17
Hello,
    Last night I was able to set up my server so that I can just connect vnc.  I even was able to be connected at the log on screen so I could select which user I wanted to log in at.  For some reason today, I have to have the monitor plugged in all the until the logon screen comes up before vnc will connect.  Once the logon screen is up, I then can connect via vnc & select which user I want to logon as.  
     It's odd because it worked last nigh, but today - Nope nada, it doesn't work & I can't explain why.  I did clean up - Removing some applications I don't need on my server. (*I'm hoping that isn't the problem*)  It's odd as well because I don't have to be logged on as a user to connect via vnc, I just have to wait until the logon screen is available...Then I can unplugged the monitor & logon.

Any thoughts on this?
~roystreet

---

### Post by Philio on 2011-02-17
It's a pain in the ***, you need a screen present for X to start properly if you want to use the default Ubuntu VNC server.

It's not hard to fix, if you Google for "headless vnc ubuntu" there are loads of guides.

---

