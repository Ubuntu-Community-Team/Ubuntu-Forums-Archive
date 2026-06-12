---
title: "KVM - how to highlight text on client terminal"
date: 2009-07-23
forum: Virtualisation
---

### Post by satimis on 2009-07-23
Hi folks,

I need to copy the text on client's (VM) terminal.  Please advise how to highlight the text with mouse pointer.

TIA

B.R.
satimis

---

### Post by Tomy on 2009-07-23
> **satimis said:**
> Hi folks,

I need to copy the text on client's (VM) terminal.  Please advise how to highlight the text with mouse pointer.

TIA

B.R.
satimis
I am interested in being able to copy from guest to host also. I found this java program but have not installed it yet.

**Remote Clip**
[http://www.cs.cmu.edu/afs/cs/user/rcm/WWW/RemoteClip/](http://www.cs.cmu.edu/afs/cs/user/rcm/WWW/RemoteClip/)
[]("http://http://www.cs.cmu.edu/afs/cs/user/rcm/WWW/RemoteClip/")

---

### Post by bodhi.zazen on 2009-07-23
If it is with a terminal , easiest way is to ssh in from your host or remote client.

You can then copy-paste commands into the terminal.

The other option would be VNC.

There are a number of apps similaer to Remote Clip , try google.

It would be nice if the KVM developers looked into this =)

---

