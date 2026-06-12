---
title: "No display on Ubuntu Server 9.10"
date: 2009-11-13
forum: Server Platforms
---

### Post by SanguineIllusion on 2009-11-13
Hi all,

I wasn't sure if this should go in absolute beginners or not. I'm not a beginner in Ubuntu but I've never worked with an Ubuntu Server before.

I recently installed Ubuntu Server 9.10 on a Dell Dimension 2350. I manage the server remotely via SSH but I've heard from someone at the physical server that the server sometimes boots with no video. I understand Ubuntu Server is meant to be headless and not have a window manager, but he should still get a terminal login screen right?

My question is: what steps should I take to help troubleshoot this? I'm the only linux guy in the company and obviously my typical strategy of grepping the X log won't work :p Any ideas?

---

### Post by mandarin77 on 2009-11-15
Just a bit of a strange question. After you set up Server and got it working, why is a monitor still connected (why waste a monitor on it)? ;-p
 
As for real advice, there have been some video driver errors noticed in the Desktop version during upgrade to 9.04 and to 9.10, and it does not seem to be hardware specific.
 
I happened to fix my issues on Desktop with apt-get. figure out which driver you have installed and remove it. (I had to restart, installed older drivers, purged, installed new version, clean, restart, repeat, not sure which specific one actually fixed it) then install the newest version again.
 
You might give that a try and see if that works for Server as well.
Hopefully you don't have hardware problems!
 
mandarin

---

