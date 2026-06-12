---
title: "video playback too fast"
date: 2012-08-07
forum: System76 Support
---

### Post by driebel on 2012-08-07
I have a new Gazelle professional, running Ubuntu 12.04, i7 processor, standard system graphics.

Often, when I stream a video online (youtube), the video plays back at ~2-3 times normal speed, with the audio obviously an unintelligible gibber.  It doesn't do this all the time, but I cannot locate the setting/issue which causes it.  Sometimes restarting (but never simply logging out) will correct the issue for awhile, but it comes back quickly.

Oh, I'm using Chrome as the browser.

Thoughts?

Dave

---

### Post by isantop on 2012-08-07
> **driebel said:**
> I have a new Gazelle professional, running Ubuntu 12.04, i7 processor, standard system graphics.

Often, when I stream a video online (youtube), the video plays back at ~2-3 times normal speed, with the audio obviously an unintelligible gibber.  It doesn't do this all the time, but I cannot locate the setting/issue which causes it.  Sometimes restarting (but never simply logging out) will correct the issue for awhile, but it comes back quickly.

Oh, I'm using Chrome as the browser.

Thoughts?

Dave

I believe this is a bug with Chrome's implementation of Flash player. You should use Chromium or Firefox until the issue is resolved upstream.

---

### Post by driebel on 2012-08-07
Hmmm, well, that did fix the "play too fast" problem, thanks!  Unfortunately, now streamed videos play in a halting, "strobe-like" manner (in both Firefox and Chromium).

Maybe a restart will clear that up...

Dave

---

### Post by isantop on 2012-08-08
> **driebel said:**
> Hmmm, well, that did fix the "play too fast" problem, thanks!  Unfortunately, now streamed videos play in a halting, "strobe-like" manner (in both Firefox and Chromium).

Maybe a restart will clear that up...

Dave

Also, make sure that you have the latest flash player installed. If it isn't installed, you can find it in software center. You'll have the latest as long as your system is up to date.

---

### Post by jdnier on 2012-08-23
I've been having the same problem with Flash video running at 2-3x speed. Although I've associated it with upgrades to Chrome, it's happening everywhere, even in Firefox. I'm now having similar stuttering with audio (e.g., Spotify's Linux client, which had been working just fine). Restarts don't seem to help. As I write this, Spotify is working fine (wasn't this morning or yesterday) but Flash videos are still running at super speed. I think that next time things start working again I'll stop applying new system updates. 12.04 has really been unstable for me. ;0

Any ideas?

---

### Post by bluename on 2012-10-17
The problem of videos playing/stuttering very quickly, like a fast-forward VHS, might be solved by disabling pulseaudio.

Try [FONT="Courier New"]pulseaudio -k[/FONT] in terminal. You should see all sound die for a second or two. See if the video plays correctly right after that. If that fixes it, it will probably start having issues again later. I used [this guide]("http://forum.pinguyos.com/Thread-How-to-Pulseaudio-and-Alsa") to replace pulseaudio with the alsa audio component, and it's worked fine for me ever since. (Ubuntu 12.04)

---

