---
title: "A3 Mania on Wine"
date: 2009-03-30
forum: Wine
---

### Post by s.kaniff on 2009-03-30
Hi, I'm trying to run A3 Mania on wine. A3 Mania is an MMORPG ([http://www.a3mania.com/](http://www.a3mania.com/)).

I am running Ubuntu 8.04 fully updated and the latest wine from the wine repo. I have an intel 965GM graphics card.

With a clean .wine folder i got some dll errors so I did the following:
'winetricks vb6run'
'winetricks mfc42'

This solved the dll problems and i was able to start the game launcher. 

The terminal output reaches something like 'fixme:d3d8:ValidateVertexShader...' and then the system completely freezes. GUI and keyboard become completely non responsive. I can only move the mouse pointer on the screen. My only option is to hard reboot the system.

AFAIK wine should never cause a system freeze no matter what. 

What am I doing wrong and how do I get this to work?

---

