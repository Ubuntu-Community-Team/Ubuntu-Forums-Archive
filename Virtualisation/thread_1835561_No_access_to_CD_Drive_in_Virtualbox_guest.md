---
title: "No access to CD Drive in Virtualbox guest"
date: 2011-08-29
forum: Virtualisation
---

### Post by slowtrain on 2011-08-29
I'm running Ubuntu as a guest with a Windows XP host in VirtualBox 4.0.12.  I simply would like to be able to read an Audio CD from within Ubuntu (so I can rip it and use RhythmBox).  But, when I insert a CD, the Windows host intercepts it and asks what I want to do.  Whether I tell it to open the CD as a folder or do nothing, I can't seem to access it from within Ubuntu.  I've tried Devices > CD/DVD Devices > Host Drive E.  That seems to simply open a copy of my ubuntu filesystem.  I then tried modifying the Storage settings in VirtualBox.  I have an empty IDE Secondary Master.  I tried adding an empty IDE Primary Master--no effect.  I can't see what else I can change.  The VirtualBox manual that I saw online (older version maybe?) talks about setting up the Host Drive and using Passthrough, but I don't see these options.

Any suggestions?

---

### Post by slowtrain on 2011-09-13
I found a solution.  I didn't see the passthrough option at first--which is why I had such problems finding it. But, go to Settings, Storage, and IDE Secondary Master.  When you click the little disk icon (which I didn't realize was clickable) and select Host Drive E:, the passthrough option appears. Once I checked it and restarted, linux can read the CD Drive. Problem solved!

I can only wish that Virtualbox would make it a little more obvious how to access that Passthrough option or even set it to Passthrough by default.

---

