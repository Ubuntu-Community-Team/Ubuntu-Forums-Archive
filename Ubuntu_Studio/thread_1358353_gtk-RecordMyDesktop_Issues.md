---
title: "gtk-RecordMyDesktop Issues"
date: 2009-12-18
forum: Ubuntu Studio
---

### Post by Bwathke on 2009-12-18
I REALLY like gtk-RMD but there is one big issue I have... If I try to record a program the screen will freeze on the first thing it sees (Such as a black screen) but whenever I move my mouse a little square takes the blacks place and puts what I want it to see... So its as if Im washing my screen :/ Any ideas?

---

### Post by Linuxforall on 2009-12-18
Set your desktop effects to none and see if the issue goes away.

---

### Post by orangemoose on 2009-12-19
Don't know if this will help. Found it trying to fix the same problem.

[http://bbs.archlinux.org/viewtopic.php?pid=670484](http://bbs.archlinux.org/viewtopic.php?pid=670484)

downgrade libtheora to 1.0-1.1. The new theora is completely different and recordmydesktop needs to be rewritten to be compatible.

---

### Post by Bwathke on 2009-12-19
> Set your desktop effects to none and see if the issue goes away. 	
I always have them off but thanks :)

> Don't know if this will help. Found it trying to fix the same problem.

[http://bbs.archlinux.org/viewtopic.php?pid=670484](http://bbs.archlinux.org/viewtopic.php?pid=670484)

downgrade libtheora to 1.0-1.1. The new theora is completely different and recordmydesktop needs to be rewritten to be compatible.

I went there and I got to the download page but it said Error 9 cannot record with this version. The download wasn't there anymore... But thanks :)

---

### Post by VertexPusher on 2009-12-21
> **Bwathke said:**
> If I try to record a program the screen will freeze on the first thing it sees (Such as a black screen) but whenever I move my mouse a little square takes the blacks place and puts what I want it to see... So its as if Im washing my screen :/ Any ideas?
Set RMD to capture full frames. Otherwise it will only capture regions that were marked as changed, and this type of change detection does not work with fullscreen OpenGL applications. Capturing full frames will fix the problem.

---

### Post by Bwathke on 2009-12-21
Thank you very much it fixed the entire problem ^^

---

### Post by suniyo on 2009-12-21
I have another problem with rmd. Video is not in sync with audio and either it runs ahead or lags behind depending upon the frame rate and other settings I choose. But still it is not exactly the way I wanted it. Any Ideas why this happen? Around 20fps it works best with 128kbps audio settings but quality is not good and filesize is too big. .ogv out put for a 5 min screen cast was 65mb. (converted to 10mb flv later.) My main problem is why AUDIO IS NOT IN SYNC WITH VIDEO?

---

### Post by VertexPusher on 2009-12-22
> **suniyo said:**
> My main problem is why AUDIO IS NOT IN SYNC WITH VIDEO?
Are you using PulseAudio?

---

