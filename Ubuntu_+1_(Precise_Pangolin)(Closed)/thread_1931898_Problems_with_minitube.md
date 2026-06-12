---
title: "Problems with minitube"
date: 2012-02-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by northwestern on 2012-02-26
Hi
Don't know if this is the right place to ask, but since downloading 12.04 the video in Minitube has stopped working. Sound appears to be normal.

Regards
Northwestern

---

### Post by exploder on 2012-02-26
I just tried minitube after reading your post. Minitube started to give me the sound from a video and then crashed to the greeter....At least you know that you are not the only one seeing this. 

I do appreciate your reminding me about this app because it might be a way around Adobe dropping support for Linux. Hopefully this will get sorted out before the final release of 12.04 and other media players are also experiencing problems right now.

---

### Post by skewty on 2012-02-26
It isn't working for me either.  Did you report it?  I reported my error.

---

### Post by exploder on 2012-02-26
I did not report this. I was waiting to see if it had already been reported first. Can you provide a link to the bug report? I would be glad to contribute to this.

---

### Post by keithpeter on 2012-02-26
+1

Never heard of minitube before, but this is called 'testing' for a reason.

My work around for watching videos on systems/internet connections that are too slow for flash is the 'unplug' firefox extension plus vlc/mplayer.

---

### Post by exploder on 2012-02-26
Minitube in the repos is not the current version. The version in the repos is 1.6 but 1.7 is currently available on the authors site. 

Also, we know this is testing but this particular application could become very popular in the near future and it may be especially useful for people using a laptop.

If there is a bug report I would like to contribute to it.

---

### Post by skewty on 2012-02-26
I believe this is the bug:

[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287]("https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/921287")

---

### Post by exploder on 2012-02-26
Thanks skewty! I posted my comments in the bug report. I really think minitube will gain in popularity in the not so distant future and it does have some very nice features. Thanks! I am really glad that this application was brought up.

---

### Post by mc4man on 2012-02-26
Here minitube, either the 1.6 in repo or 1.7 from site doesn't crash but both have significant issues. Seems they'll play some video's, usually music ones, but for most nothing or just sound.

What does work very well is the 1.7 version, (pre-built binary) with  phonon-backend-gstreamer removed & phonon-backend-vlc installed instead

So at least here the issue is with gstreamer, not minitube

This is also confirmed here by extracting the repo minitube_1.6-1_i386 package, taking the minitube binary (1.6) out & running it. 
 It also works just fine with phonon-backend-vlc

---

### Post by exploder on 2012-02-26
mc4man, would you consider adding what you have found to the bug report? I mentioned in the report that their was a newer version of minitube available but what you have discovered might be what is affecting other media players as well.

Edit: I went ahead and added the information to the bug report, it might help with this bug and similar issues with other media players as well.

---

### Post by mc4man on 2012-02-26
I think the crash & the current crappy performance with the gstreamer backend (at least on an Ubuntu install), are separate issues

So starting/using  minitube 10 times here with the vlc backend - it segfaulted once, (the reported crash) & worked _perfectly_ the other 9 times

If anyone has occasion to try either the 1.6 or 1.7 with the vlc backend that would be interesting to see if performance also improves 
(easy to do, ask if unsure how

---

### Post by mc4man on 2012-02-26
It's appears here to be a gstreamer decoding issue, some videos are ok, some can't be properly decoded thru gstreamer, that's why the vlc backend works.

Taking a look at the files while in tmp shows the ones that play back without video are avc1 either  Baseline@L2.1 or  Baseline@L1.1, ones that do are all  Baseline@L3.0

This was checked against a number of videos & was consistent

Additionally causing totem to try to play the streams showed same behavior or worse, only the Baseline@L3.0 streams were playable 
(also only the Baseline@L3.0 files will  get thumbnails, the others only a video icon 

So the playback issue is clearly with gstreamer, whether decoding issue also contributes to a crash is unclear

---

### Post by mc4man on 2012-02-27
After a bit of checking this 'gstreamer' decoding issue may just be for certain youtube videos that are encoded as mentioned above & maybe another 1 or 2 variations.
(grabbed some similarly encoded video from Interent archives & totem had no issue, additionally playbin does decode the currently failing youtube types

It's a hard bug to file against gstreamer & or totem which also fails to decode due to providing sample files.

One can get a url that minitube uses for testing in totem but the url's are time based & expire (maybe last one day?, so no use posting/attaching to a bug report
The only other way is to talk about tmp ect. which is discouraged so won't

Maybe this resolves itself, maybe not - one useful option would be to have minitube allow either backend - 
[https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586](https://bugs.launchpad.net/ubuntu/+source/minitube/+bug/941586)

---

