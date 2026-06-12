---
title: "Video/audio sync problem in kdenlive"
date: 2009-07-20
forum: Ubuntu Studio
---

### Post by Nixie Pixel on 2009-07-20
Hi, I am having very bad audio/video sync problems in kdenlive 0.7.5 with Jaunty.

The first time I play the audio in the project monitor, there is no issue, but if I move along the timeline manually, the sound gets out of sync, and progressively worse each time I move. This is while trying to work with .wmv files.

This post in another forum seems to indicate that it is not just a problem with kdenlive, but that kino also has this problem:

[http://www.kdenlive.org/forum/075-ubuntu-intrepid-sound-delay-bug](http://www.kdenlive.org/forum/075-ubuntu-intrepid-sound-delay-bug)

Any ideas what could be causing this?

Thanks!

---

### Post by hansdown on 2009-07-20
Hi Nixie Pixel.

Are you using pulse audio? There are suggestions to use alsa as a fix.

[http://www.kdenlive.org/user-manual/troubleshooting-and-common-problems/sound-bad-and-delayed](http://www.kdenlive.org/user-manual/troubleshooting-and-common-problems/sound-bad-and-delayed)

---

### Post by Nixie Pixel on 2009-07-20
Hi, thanks, I tried that already and am only using ALSA. It hasn't made a difference.

---

### Post by hansdown on 2009-07-20
> **Nixie Pixel said:**
> Hi, thanks, I tried that already and am only using ALSA. It hasn't made a difference.

Sorry,I should have seen that. Sometimes I try to skim a few links.

Go to```
 Settings->configure Kdenlive->default project->DV NTSC
```

Hope this helps.

---

### Post by Nixie Pixel on 2009-07-21
That doesn't help, but thank you for trying!

I did confirm that the problem isn't in kdenlive itself though, or so I believe - the sync problem happens even when I am just using the clip monitor, without putting the clip on the timeline. So isn't that an ffmpeg problem, or melt problem?

Thanks!

---

### Post by Nixie Pixel on 2009-07-21
This link seems to indicate a potential problem, something about .WMV being variable frame rate?

[http://avidemux.org/admForum/viewtopic.php?id=5965](http://avidemux.org/admForum/viewtopic.php?id=5965)

Could there be something that helps in that thread?

Thanks!

---

### Post by Nixie Pixel on 2009-07-21
I was able to avoid the sync problems by using ffmpeg to transcode to .mp4 format, vcodec h.264, acodec aac.

This is definitely not ideal since it adds loss to the video. I would love to find out a way to work with the .wmvs directly.

Though in the future I will find a way to record in a different format, for now I'm stuck with .wmv.

---

### Post by hansdown on 2009-07-21
Good call on the ffmpeg Nixie Pixel.

I've been looking at a bug report. Maybe an update coming in the near future?

[http://www.kdenlive.org/mantis/view.php?id=865](http://www.kdenlive.org/mantis/view.php?id=865)

---

