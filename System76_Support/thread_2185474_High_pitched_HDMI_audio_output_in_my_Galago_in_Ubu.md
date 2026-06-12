---
title: "High pitched HDMI audio output in my Galago in Ubuntu 13.10"
date: 2013-11-02
forum: System76 Support
---

### Post by javsalgar on 2013-11-02
Hello everyone,

After reinstalling Ubuntu 13.10 in my Galago I am experiencing the following problem. I can see the HDMI Output and the video output works fine. The audio works as well, but the pitch is very high (making impossible to watch a film, for example, as every voice sounds as if they were smurfs or something xD). 

Any ideas about this problem?

Thank you in advance

---

### Post by beru2 on 2013-11-25
I appear to be having the same problem, though I'm running Arch. Anyone have an idea as to what could be causing this?

---

### Post by raphael-estrada on 2013-11-26
Noticed that I'm having this, too. Could have been going on for a few days now, didn't notice cause wasn't playing audio/video.
Seems like my flash plugin (both in chrome, FF) is playing sound at double speed. This defo worked in 13.10 for me, too. Must be a recent update or something...

Any ideas?

---

### Post by raphael-estrada on 2013-11-26
Update: Appears to affect Rhythmbox music, too. So probably pulse related or something, not just flash...

---

### Post by raphael-estrada on 2013-11-26
... and works fine with normal speakers (not HDMI).

---

### Post by beru2 on 2013-11-26
Mine only happens over HDMI, and affects both XBMC and VLC, so I'm assuming it's pulseaudio, as well. I'm running gnome 3.10 on 64 bit Arch. (Obviously on a Galago)

---

### Post by raphael-estrada on 2013-11-27
Can anyone from System76 confirm this to be an issue with a recent update to pulseaudio or something?

---

### Post by isantop on 2013-11-27
I haven't seen this issue specifically. I'm waiting on a response from the system engineer to see if he knows anything, and I'll be doing individual testing this weekend.

---

### Post by raphael-estrada on 2013-11-27
Thanks. I've already been having HDMI audio issues (a still open support case, no progress there) and this is just making those cases where it works a pain :-/

---

### Post by golfdiesel on 2013-12-01
> **raphael-estrada said:**
> Thanks. I've already been having HDMI audio issues (a still open support case, no progress there) and this is just making those cases where it works a pain :-/

What kind of HDMI audio issues? My Gazelle Pro does not output audio over HDMI in 13.10 but it does in 13.04 with the proper intel drivers.

---

### Post by beru2 on 2013-12-04
Just wanted to chime in and say that the problem's been fixed for me. Was probably a kernel bug or something: one of the past updates fixed it.

---

### Post by raphael-estrada on 2013-12-05
> **golfdiesel said:**
> What kind of HDMI audio issues? My Gazelle Pro does not output audio over HDMI in 13.10 but it does in 13.04 with the proper intel drivers.

Yes, my Galago had problems with HDMI audio. One some TV/monitor it's typically fine, sometimes the audio is reeeeally low volume (if I max up the active speaker system, I'd hear the sound very faint). On one TV it just won't work anymore at all. I suspected some cached profile settings with wrong values in pulse or alsa, but never go anywhere. Will try a live CD on the "broken" screen to see if there's a difference.


> **beru2 said:**
> Just wanted to chime in and say that the problem's been fixed for me. Was probably a kernel bug or something: one of the past updates fixed it.

Confirmed, HDMI audio pitch is fine now.
Set to be [SOLVED]?

---

### Post by beru2 on 2013-12-05
> **raphael-estrada said:**
> Yes, my Galago had problems with HDMI audio. One some TV/monitor it's typically fine, sometimes the audio is reeeeally low volume (if I max up the active speaker system, I'd hear the sound very faint). On one TV it just won't work anymore at all. I suspected some cached profile settings with wrong values in pulse or alsa, but never go anywhere. Will try a live CD on the "broken" screen to see if there's a difference.




Confirmed, HDMI audio pitch is fine now.
Set to be [SOLVED]?

Oddly enough, the problem happened again. I plugged the HDMI cable into my computer and, after about 15 minutes worth of tinkering with programs like XBMC and Steam Big Picture, something must have gone awry because the problem returned. I restarted the machine and it was gone, again. So, not necessarily solved, but not necessarily a huge problem. I'll troubleshoot it some more if it happens again.

---

### Post by raphael-estrada on 2013-12-06
Yup, happening again here, too.

That would've been too easy, right?

---

### Post by raphael-estrada on 2013-12-07
I'm beginning to realize what a clusterf*** audio on Ubuntu seems to be... so many moving bits, no idea what's going on here.

---

### Post by beru2 on 2013-12-08
> **raphael-estrada said:**
> I'm beginning to realize what a clusterf*** audio on Ubuntu seems to be... so many moving bits, no idea what's going on here.

As I said earlier, I'm on Arch. My audio stuff isn't that complex: I have ALSA and Pulseaudio. The problem is either with one of those, or the driver provided by the kernel.

---

### Post by raphael-estrada on 2014-01-18
This is still happening. Please let me know what to do here.

---

### Post by vange on 2014-03-28
This is happening to me on Ubuntu Gnome 13.10 on Lenovo T440p

---

### Post by mervinb on 2014-04-11
I am seeing this problem on a Dell XPS15 (the new Haswell QHD+ video model). Although I'm using Arch, I'm posting here are the symptoms are identical (and I use Ubuntu on my desktop ;);) ).

When using mpv to play a video, even if display is via HDMI, if sound is via the built-in speakers, the speed of video the pitch of the audio are normal. When pavucontrol is used to switch audio to HDMI, the video playback speeds up a little and pitch is raised. This happens *both* on 3.13 and 3.14 kernels, and the same Intel driver (I'm not using the nvidia card).

It is a fairly serious problem, and should get attention, where where should it go to, as my guess is that it's upstream, either with kernel or xf86-video??

---

### Post by mathsguy on 2014-04-16
> **isantop said:**
> I haven't seen this issue specifically. I'm waiting on a response from the system engineer to see if he knows anything, and I'll be doing individual testing this weekend.


Galapago Ultra Pro. Ubuntu 13.10. I have the same issue. HDMI audio sounds like the chipmunks.

any news on this issue?

---

### Post by allcoms on 2014-05-15
I'm getting high pitched, distorted audio out via HDMI on my Gazelle Pro (i4600 GPU) under both 3.13.10 (Deb Jessie) and 3.11.0 (Ubuntu 12.04.4) kernels/OSs.

I've brought this up on the ALSA dev list. This thread [https://bugzilla.kernel.org/show_bug.cgi?id=60769](https://bugzilla.kernel.org/show_bug.cgi?id=60769) seems to indicate this could be fixed in kernel 3.14 but I've not tried that yet.

---

### Post by Yann-Baol on 2014-05-20
+1, Ubuntu 14.04 fresh install udated the 19th of May, i3-4000M (intel  HD4600 GPU). HDMI delivers (when it delivers something) a high pitched  audio. It looks like 44.1KHz rate audio is streamed at 48KHz rate. E.G.  with Rythmbox, track time is speed up and sound is sensibly high  pitched, with VLC it slightly different I have high pitched chopped  sound. When using internal speaker ith analog card evrything is fine. 
I fail (no sound) to feed anything sampled at 48KHz as well to HDMI at  pulse level or directly to alsa (plughw or hw), while it works when  connected to analod audio card.
I have also tried to force ate conversion to 48KHz either in Pulse or alsa without success (broken stream). 
It seems issue is more likely at alsa driver layer side.

---

