---
title: "RDP &amp; WinXP"
date: 2005-11-16
forum: Requests
---

### Post by buddy420 on 2005-11-16
Recently installed Ubuntu 5.10; I haven't used *nix since 9 yrs ago (Redhat Fedora was just coming out and I was a co-op student guinea pig'd to Slackware...) so am refreshing myself with more current situations of what I can do with the o/s in terms of offering solutions for clients requests.  What options are available to remotely access with a gui (from WinXP > Ubuntu box) ?

Links to any resources appreciated

cheers

---

### Post by stuporglue on 2005-11-16
VNC is probably the most cross-compatable. There are VNC servers and viewers for almost any platform. 

I don't think they forward sound though, if that's an issue. 

Welcome back!

---

### Post by rmjokers on 2005-11-16
I use tsclient on breezy to connect over RDP to a windows 2003 server box.  It does allow for sound forwarding if you use the rdpv5 protocol, but the sound is a little bit choppy.

---

### Post by buddy420 on 2005-11-16
Ubuntu has the client for TS, what about the server application?

Sound is optional for me, only use I'd have is to check if a media file is corrupt and not the radio stream that's intermittent with connection fluxuation.

cheers

---

### Post by bur[n]er on 2005-11-18
As far as remote server goes, you can use vino.  It's the default vnc server for Gnome.  When logged in, System -> Preferences -> Remote Desktop, to set up the options.

---

