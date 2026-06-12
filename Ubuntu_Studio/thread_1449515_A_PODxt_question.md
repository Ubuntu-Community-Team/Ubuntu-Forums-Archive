---
title: "A PODxt question"
date: 2010-04-07
forum: Ubuntu Studio
---

### Post by tava0002 on 2010-04-07
I don't know if this is the best place to post this but here goes.

I have my PODxt working, I can record with Ardour and hear my guitar though my monitors.  I can't get the Line6 Edit working with Wine, Line 6 Edit is the UI for the POD which makes life much easier. When I open it, it becomes unresponsive and I have to kill it.
 
My question is if there is a known good UI for the PODxt or if anyone can get the Line6 GUI to work with Wine.

---

### Post by cptncatholic on 2010-05-31
Unfortunately, I don't know about getting the Line6 Edit working in Wine. I have heard that Wine doesn't support USB devices, so that could be the issue there. If you have a winxp install cd, you could download Virtualbox (use the full version from here - [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

or use: 
```
sudo apt-get install virtualbox-3.2 dkms
```

Then set up a winxp virtual machine, be sure to enable USB support and then install all the Line 6 software you need. 

It's not ideal . . . it's cheating in a way. You're still having to rely on winxp to get the job done. It would be nice if Line 6 would just support Linux users, but that ain't happenin'.

My question for you is about getting the PodXT set up in Linux to record. I've been trying to get Ubuntu Studio 9.10 to recognize my Pod XT Live and I can't get anywhere with it. Do you recall how you got your Pod XT to record with Ubuntu?

Thanks!
tc

---

