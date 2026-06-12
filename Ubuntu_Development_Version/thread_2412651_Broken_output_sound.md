---
title: "Broken output sound"
date: 2019-02-15
forum: Ubuntu Development Version
---

### Post by dino99 on 2019-02-15
Today sound output is broken on DD: 
when i check sound gnome settings, i only have a 'dummy output' choice.
will try downgrading some of the latest proposed packages, and report back soon.
this has happened with the disco boot with '13' kernel; previously i have upgraded bionic and cosmic releases.

Back to Disco, that time i boot on the previous '12' kernel, and sound is ok. Rebooting with the latest '13' kernel, and the sound is also ok now  :p

Cant say what was wrong , with the previous sound problem  the journal had  logged : pulseaudio[1548]: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0"

---

### Post by jbicha on 2019-02-15
There were updates to pulseaudio and gst-plugins-good1.0 this week. Maybe rebooting was all you needed.

If the issue comes back, please report a bug.

---

### Post by Kris_M on 2019-02-15
new kern 4.19.0-13 no sound from headphones after reboot UNLESS unplug/replug. Then fine.

EDIT: No, you're right - not the kern, it's alsa. (i.e. previous kern does same thing)

EDIT2: further, if boot w/o headphones, no sound - plug in headphones get sound. If unplug at that point, still get sound.
Plugging/unplugging wakes something up.

I do not know how to file a bug. If I get help, I will. This just happened this morning.
Never mind, I just logged in to launchpad and will file bug.
EDIT nope, in launchpad and don't know where to start.

I have no idea what I should do in there, but found this:
[https://bugs.launchpad.net/qemu/+bug/1816052](https://bugs.launchpad.net/qemu/+bug/1816052)
4 hours ago.
added comment.

---

### Post by dino99 on 2019-02-15
Kris, report your own bug; from a terminal: >  ubuntu-bug gst-plugins-good1.0

Could be related to that 'back-out' feature:

gst-plugins-good1.0 (1.15.1-1ubuntu2) disco; urgency=medium

  * Cherry-pick Revert-pulsesrc-Move-to-extended-stream-API.patch:
    - Back out a feature that depends on an unreleased PulseAudio
      feature and broke audio recording (LP: #1815670)

 -- Jeremy Bicha <jbicha@debian.org>  Tue, 12 Feb 2019 23:15:55 -0500

---

### Post by Kris_M on 2019-02-15
> **dino99 said:**
> Kris, report your own bug; from a terminal: 

Could be related to that 'back-out' feature:

gst-plugins-good1.0 (1.15.1-1ubuntu2) disco; urgency=medium

  * Cherry-pick Revert-pulsesrc-Move-to-extended-stream-API.patch:
    - Back out a feature that depends on an unreleased PulseAudio
      feature and broke audio recording (LP: #1815670)

 -- Jeremy Bicha <jbicha@debian.org>  Tue, 12 Feb 2019 23:15:55 -0500

Nope.
I first experienced this this morning. This evening i tried to get it to play audio over hdmi and it no longer would. (would yesterday).

---

### Post by dino99 on 2019-02-16
Try:
> ubuntu-bug gstreamer1.0-plugins-good

---

### Post by Kris_M on 2019-02-16
Sorry for delay but i think they fixed it.
Last night I went back 6 days (Macrium) and then updated everything except the alsa stuff ( many libraries and some command line stuff) and it still worked fine.
Got your note this morning and went to update the new stuff excluding the alsa stuff, but it installed everything anyway, rebooted, and it works fine.
I think there was stuff in either libraries, or base that were bad as I didn't see them this morning.
We'll probably see that stuff again, hopefully corrected, as they have to fix the bad updates for the rest of the folks that took it.
EDIT - just checked external monitor (HDTV), and sound transfers correctly there as well, so all is right with alsa at the moment.  I'll have to remember to back up before taking any more alsa updates for a week or 2!

---

### Post by Kris_M on 2019-02-16
Just took an update (didn't see any alsa) and got prob again. This time used your 
ubuntu-bug gstreamer1.0-plugins-good
 and filed bug. Thanks!

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1816271/comments/0](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1816271/comments/0)

---

### Post by Kris_M on 2019-02-16
screenshots of sound: after boot, and then after I unplug/replug headphones.

---

### Post by dino99 on 2019-02-17
Your screenshots are the same as mines when i've got that issue.
How it had happened on my system:
- a couple days ago, made the usual daily upgrades from 'proposed', including gvfs, pulseaudio,  alsa and the likes. Sound was working before and after the upgrades.
- with the next cold boot, i first upgrade some other releases (bionic, cosmic, bulleyes), the sound was was ok on each ones.
- next cold boot on Disco, kernel 13, and that sound issue appeared; i've closed and reopened the session, but that did not solved the problem.
- rebooting with the kernel 12 and there the sound was ok; in fact i should say that the system had found and well identified the mobo sound chipset.
- since, i have made many cold boots and  sound is now always working.

So it looks like the upgrade process has disturbed, at boot time, the sound chipset discovery;  is it the gcc8/9 switch to blame ?

---

### Post by Kris_M on 2019-02-17
If you add that info to bug, that might help - they have no idea now.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1816271](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1816271)

---

### Post by dino99 on 2019-02-17
I cant post on launchpad due to an issue; so its easier for you to post that thread link instead. :(

---

### Post by Kris_M on 2019-02-17
done.

as in banned? bummer.

---

### Post by Kris_M on 2019-02-19
I believe I have also caught Software Updater updating stuff that you have unckecked, anyway. I believe this will happen on second and subsequent updates within a cold boot. I was not able to control it the way I thought I could. reboot before you take an update...  later tater.

AHA I think we're getting somewhere - like a pulseaudio that went in on the 14th...

Back to the beginning, but that, in itself, is progress.

---

### Post by Kris_M on 2019-02-20
I believe it's fixed
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1816271](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1816271)
May have to go to settings/sound and set things up initially.
They now hold through boot.

Please mark this thread as solved if you are content with this @dino99 (and many thanks for your help filing the bug!!!)

---

