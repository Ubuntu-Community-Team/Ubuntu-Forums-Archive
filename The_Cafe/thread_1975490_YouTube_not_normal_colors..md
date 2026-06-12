---
title: "YouTube not normal colors."
date: 2012-05-07
forum: The Cafe
---

### Post by KL_72_TR on 2012-05-07
Hello.
I'm posting this here because I'm only curious.
It is some weeks now that all videos in YouTube (and only in YouTube) are not with their normal colors.
To be more specific: all the people appear blue, everything that normally is red now is blue, the sky also has a different color.
What I'm saying is that nothing anymore is in the normal colors as **before (some weeks ago).**
I would like to know if this problem is happening only to me or not.

---

### Post by llua+ on 2012-05-07
disable hardware acceleration in flash.
right click the video > settings > untick 'enable hardware acceleration`

---

### Post by Bandit on 2012-05-07
Having same issue here across multiple distros. Cant seem to disable hardware accleration as the setting dialog just freezes while video keeps playing... /sigh

Good news is Youtube now is using HTML5 on newer videos.

---

### Post by LADmaticCA on 2012-05-07
You can set it by creating an mms.cfg file in /etc/adobe/ that reads:

```
EnableLinuxHWVideoDecode=0
OverrideGPUValidation=true
```

This fixes the color for me on youtube but unfortunately makes flash crashy for other sites. Adobe really screwed this one.

I have been using and enjoying the FlashVideoReplacer addon...high quality, embedded, smooth youtube playback.

---

### Post by Uncle Spellbinder on 2012-05-07
> **llua+ said:**
> disable hardware acceleration in flash.
right click the video > settings > untick 'enable hardware acceleration`

This works. If you can't untick the option, refresh the page and view in full screen and try again. Should work fine.

See here: [http://ubuntuforums.org/showthread.php?t=1966262](http://ubuntuforums.org/showthread.php?t=1966262)

---

### Post by mehaga on 2012-05-08
[This]("https://neanderslob.wordpress.com/2012/04/23/fixing-blue-tint-in-youtube-videos/") worked for me. In short, you do this:

sudo mkdir /etc/adobe
echo -e "EnableLinuxHWVideoDecode=1\nOverrideGPUValidation=true" | sudo tee /etc/adobe/mms.cfg > /dev/null

Colors are back, but flash crashes from time to time. 

[This]("https://www.youtube.com/html5") works very well, but  not all videos are supported (falls back to flash for unsupported videos, so you still need a solution for flash).

---

### Post by jespdj on 2012-05-08
It's [a known bug](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/968489), probably in the NVidia driver or in Flash.

Very annoying, I hope it gets fixed soon...

---

### Post by chugtairizwan on 2012-05-08
I read all the threats, and really it's very informative for me, for you tube video you need to disable acceleration.:popcorn:

---

### Post by iMurshaq on 2012-05-08
> **Bandit said:**
> Having same issue here across multiple distros. Cant seem to disable hardware accleration as the setting dialog just freezes while video keeps playing... /sigh

Good news is Youtube now is using HTML5 on newer videos.

True, but you can't watch videos with ads with HTML5 because YouTube has not updated the ad system to work with HTML5

---

