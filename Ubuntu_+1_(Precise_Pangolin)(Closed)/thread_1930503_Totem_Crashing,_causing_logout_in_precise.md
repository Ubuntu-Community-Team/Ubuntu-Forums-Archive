---
title: "Totem Crashing, causing logout in precise"
date: 2012-02-23
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by defconoii on 2012-02-23
Totem movie player is logging me out each time I open a video, this doesnt happen with vlc, anyone else experiencing this issue, is it a bug or could I have a package that is scewing this up due to user error.  

Also setting default video player in Settings->Info  doesn't save, selecting open with app does however.  I uninstalled totem for now until this is resolved

Also this is unrelated, but I am unable to burn audio cd's with brasero because it cant decode the mp3's, k3b however does with extra-codecs

---

### Post by cariboo on 2012-02-23
Have you got ubuntu-restricted-extras installed?

---

### Post by jbicha on 2012-02-23
What version of Totem are/were you using?

---

### Post by mc4man on 2012-02-23
> **defconoii said:**
> 
Also setting default video player in Settings->Info  doesn't save, selecting open with app does however.  I uninstalled totem for now until this is resolved

The 'Default' settings there only sets the app chosen to 1 specific mimetype so in the case of Video & Music not all that useful, also  note that the new place to find isn't "Info", it's now "Details" - so are you up to date?

(the types for Video & Music are respectively
video/x-ogm+ogg
audio/x-vorbis+ogg

---

### Post by defconoii on 2012-02-25
Totem is crashing with fglrx drivers as well as the ati catalyst drivers only with a dual monitor setup, I think it has to do with the accelerated overlay, because when I disable that in VLC im able to watch videos with vlc only, just not totem.

---

### Post by Gregory Lee on 2012-02-25
I have the fglrx driver (one monitor), and Totem, VLC, SMPlayer, mplayer, all log me out when I attempt to play a video.  I installed the restricted extras package.

---

### Post by t1497f35 on 2012-02-25
Since upstream Totem already depends on clutter - does Canonical plan to keep Totem at version 3 forever to avoid clutter?

---

### Post by mc4man on 2012-02-25
> **t1497f35 said:**
> Since upstream Totem already depends on clutter - does Canonical plan to keep Totem at version 3 forever to avoid clutter?

Here's short explain on that, I'd suspect 12.10 will move forward one way or the other
[http://jeremy.bicha.net/2012/02/01/gnome-versions-for-ubuntu-1204/](http://jeremy.bicha.net/2012/02/01/gnome-versions-for-ubuntu-1204/)

---

### Post by t1497f35 on 2012-02-26
Thanks,
there's no mention about what's the plans with clutter/totem but I hope totem3+/clutter will be in for the next release.

---

### Post by Kenda on 2012-03-18
I have this crash too. Both with Totem and VLC using fglrx with dual monitor set up

---

