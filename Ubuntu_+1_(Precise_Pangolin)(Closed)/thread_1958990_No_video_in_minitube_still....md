---
title: "No video in minitube still..."
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by exploder on 2012-04-15
Is anyone else getting video playback in minitube? Minitube will give me some audio and I can download most of the videos I want before it crashes but I have not been able to get the videos themselves to work in minitube.

Totem will not play the downloaded videos either though that's not a real problem here because I use VLC and it seems to play mp4 files just fine. 

With everything that is going on with Adobe Flash I think apps like minitube might be of real help to us in the future.

---

### Post by mc4man on 2012-04-15
For the most part have fixed here though not much indication that it will be in general though maybe it will just start working again

There is rhe crash bug which can be mitigated for the most part by switching backends from gstreamer to vlc
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287)

Except as packaged you can't without changing minitubes control file
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

The issue with gstreamer thru minitube & also seen by trying to play those files directly in totem is here
[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/973014)

So atm you can either get the precompiled binary or the source code & build or unpack the 12.04 minitube deb, edit the control file,  repack & install
Then you'd remove the gstreamer backend & install the vlc one

---

### Post by exploder on 2012-04-15
Thanks for the response. I had a feeling this was related to the gstreamer packages. I have seen these same problems appearing in other distros as well and I am hoping this will work itself out pretty soon. I have been keeping my installs stock other than adding the additional apps I like to use. If the bug is not resolved when 12.04 goes final I will of course use your suggestions to get things working like they should but for now at least I know that I am not the only one seeing this bug. Thanks!

---

### Post by mc4man on 2012-04-15
There are some vid's that won't play even with the vlc backend, whether on minitube or 12.04 not sure, would have to try the exact same in 11.10

---

### Post by exploder on 2012-04-15
minitube worked fine for me in 11.10. I noticed that the version in the repos is out of date but both the current and latest versions would work in 11.10.

---

### Post by mc4man on 2012-04-15
Just switched to my new install & the couple that weren't working with the vlc backend are now ok, 
(they are showing with the default video thumbnail in 'you know where but we won't mention'  but fine in minitube - screen

---

### Post by exploder on 2012-04-15
mc4man, I appreciate all of the information you have posted. I see the status on the bug is set to medium, so the odds on this getting fixed look pretty good. It is also good to know that the issue can be worked around if needed. Minitube is real handy and the download feature makes it a pretty valuable application for me.

---

### Post by mc4man on 2012-04-15
Figured out what was wrong on my 32 bit install - long story short the gstreamer backend was still installed even though synaptic wasn't showing when I first looked (why don't know), anyway all is good now

If they don't fix this one way or the other then let me know - there are as I said many options to fix this as a user, some only take about 30 sec's or so

---

### Post by xebian on 2012-04-15
Out of curiosity I just installed minitube and seems to be working ok - online and totem (movie player?) plays the downloaded video.  Had to search where it is as minitube seems to have no preferences configuration from it's menu?

---

### Post by exploder on 2012-04-15
Thanks mc4man! I appreciate your offer to help and I might end up taking you up on it. Minitube has become one of my most used applications for collecting my favorite music videos and with Adobe no longer providing new versions of Flash for Linux minitube will only gain in popularity.

---

### Post by mc4man on 2012-04-15
> **xebian said:**
> Out of curiosity I just installed minitube and seems to be working ok - online and totem (movie player?) plays the downloaded video.  Had to search where it is as minitube seems to have no preferences configuration from it's menu?

It's not all youtube vid's - the no video issue is mainly with ones encoded as AVC 1 Baseline@L2.1, Baseline@L1.1 & some others @ 3.0
(I attached a small test clip to the decoding bug - it will not play in gstreamer on 12.04, will in gstreamer in 11.10 & earlier & with any non gstreamer player 

Additionally the gstreamer backend is more prone to crashing when switching vids before they've finished playing

Just to note - Umplayer has an excellent youtube feature that works quite well - not in the repo's but .deb's here. Umplayer is an improved smplayer, also note smplayer itself has improved 

[http://www.umplayer.com/download/](http://www.umplayer.com/download/)

---

### Post by xebian on 2012-04-15
> **mc4man said:**
> It's not all youtube vid's - the no video issue is mainly with ones encoded as AVC 1 Baseline@L2.1, Baseline@L1.1 & some others @ 3.0
(I attached a small test clip to the decoding bug - it will not play in gstreamer on 12.04, will in gstreamer in 11.10 & earlier & with any non gstreamer player 

Additionally the gstreamer backend is more prone to crashing when switching vids before they've finished playing

Sorry.

---

### Post by mc4man on 2012-04-15
> **xebian said:**
> Sorry.
Nothing to be sorry about - as you've seen it still does work ok, just depends on the vid's chosen

---

