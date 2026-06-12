---
title: "LibStdC++6 From Lenny installed broke Synaptic , Package Dependency Resolve fix"
date: 2009-11-17
forum: Server Platforms
---

### Post by Ocelaris on 2009-11-17
So I made a boo boo, I was trying to install Symantec Backup Exec software for a client, which supposedly runs on Debian Lenny, and it required LibStdC++6 and I installed a Lenny Package over the Ubuntu one... So it has all sorts of broken dependencies, and if I go through the command line choices of "fixing" they pretty much all involve keeping the broken package and uninstalling EVERYTHING ELSE! meaning basically it would destroy the system to keep the bad package.

*I figured it out though, and just though I would share for those in my wake, because I searched for weeks for a fix and just came across it. 

Use the GUI synaptic package manager, and search for "broken" packages, filter for broken. And in my case, I over wrote the Ubuntu LibStdC++6 library, and I was able to view "properties" and see there was a previous jaunty version. So I went back to the package, and "forced previous version" from the menu and it reverted, and now all my dependencies are fixed!

Synaptic saves again!

---

### Post by jbroome on 2010-06-07
So how did you get around the libstdc++5 requirement for backup exec?

---

### Post by Ocelaris on 2010-06-07
I didn't, it didn't get installed. I just used native sql client to dump mysql and samba fileshare dumps. Sorry, not a good answer, but that project kinda went by the wayside, and was over budget for what they wanted.

---

### Post by jbroome on 2010-06-08
Gotcha!  Thanks a bunch for the followup answer.

---

