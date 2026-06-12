---
title: "Ubuntu studio + line6 pod xt"
date: 2008-11-14
forum: Ubuntu Studio
---

### Post by cyrus_the_virus on 2008-11-14
Hi,

I have line6 pod xt live. It currently doesn work in ubuntu 8.10 because the linux drivers require ALSA which isn't installed anymore on 8.10.
I was wondering if Ubuntu Studio uses ALSA? If yes, can I install ubuntu studio from synaptic in the 'normal' ubuntu?

Greets,
Martin.

---

### Post by 98springer on 2008-11-23
Ubuntu Studio can use ALSA although I think that by default 8.10 comes with pulseaudio which you can disable and use ALSA. There are some posts on here about disabling pulse and installing ALSA. I tried adding Ubuntu Studio in the past and for me (being a newb) it was easier just to start from scratch and let the installation detect everything and be done with it.

I'm looking for a way to control the Pocket Pod with Linux. What were you using?

---

### Post by cyrus_the_virus on 2008-11-24
hi,

thanks for your reply. I'm using a line6 POD XT Live. The linux drivers ([http://www.tanzband-scream.at/line6/]("http://www.tanzband-scream.at/line6/")) use to work perfectly in ubuntu 7.10. I was able to record and playback through my pod with no (noticable) delays after doing the ubuntu studio preparation guide ([https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation"))

In 8.04 the driver would not compile because of missing alsa modules. A couple of days ago I gave it a go in ubuntu 8.10 (not studio) and it did compile and I was able record with it. Playback was also possible but the sound was very scratchy.
Anyway, I have another problem in 8.10. If I install the realtime kernel on it (as described in the ubuntu studio preparation guide) my nvidia driver won't work anymore.
I'm still considering installing ubuntu studio. Does somebody know if the pod xt driver works in ubuntu studio? If I have time I will give it a try myself.

About the pocket pod, I don't know if the drivers I use for my pod xt in linux will work the pocket pod. But you can try (check the first link in this post)

---

