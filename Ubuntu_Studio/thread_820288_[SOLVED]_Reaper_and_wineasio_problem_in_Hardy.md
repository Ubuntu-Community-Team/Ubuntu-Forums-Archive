---
title: "[SOLVED] Reaper and wineasio problem in Hardy"
date: 2008-06-06
forum: Ubuntu Studio
---

### Post by eric71 on 2008-06-06
I've been experiencing an odd problem with wineasio and reaper, which used to work well before upgrading to hardy. 

Initially, I ran into the tickless kernel issue with the realtime kernel. Reaper was running, but I was getting terrible performance from jack. Once the nohz=off boot solution was announced, I ammended my grub entry and jack was happy once again. Now, unfortunately this seems to have caused a wine/reaper related problem. Reaper is locking up toward the end of project loading - i.e. before the splash fades away. This doesn't happen with the normal kernel, but of course jack performance sucks.

I used Sidux (Debian unstable) for a few days with their new rt-kernel, and did not have this problem. What could be happening in Ubuntu with wine and Reaper to cause this? I installed Kubuntu over Sidux last night to try the latest release of Reaper, and no pulseaudio, but had no better luck. Sidux, for the small amount I worked with it, seemed great for audio production. I just missed that little bit extra polish and user-friendliness (and huge support community) and would prefer if I can get this problem sorted in Ubuntu. 

Thanks,

Eric

---

### Post by eric71 on 2008-06-07
I'm beginning to think that this has someting to do with a vst not playing nice. Possibly freeamp3, which I had been using a lot of, often multiple instances per project. I've managed to re-create the crash in pclinuxos, which I had thought was working. I'm having another go with kubuntu and will see if I'm right about this.

---

### Post by eric71 on 2008-06-08
Another update...

Still crashing in Kubuntu. It's funny, because Making Me Nervous will play fine. It's just old projects that seem to be causng some massive cpu or memory usage problem near the end of project loading. These are projects that were mostly recorded in Kubuntu within the last 6 months. I'm beginning to wonder if there is a combination of the latest versions of reaper and vsts that aren't working out with wine and the latest rt-kernel. Tomorrow I'll try an old 1.X build of reaper and see if that makes a difference. Or maybe back to Sidux for some more playing around. The fact that a lot of people use Reaper on Ubuntu with wineasio, and nobody else seems to be having this problem here or on the Reaper forums leads me to believe there's a problem cropping up from one of the mountain of free vsts I use. Wasn't freeamp3 though.

---

### Post by eric71 on 2008-08-27
Using the latest RT kernel in a recently installed 8.04.1 with the latest Reaper, all is good now. Never really figured it out, but my BIAB, wineasio, Reaper songwriting/demo making combo is working better than ever in Ubuntu.

---

