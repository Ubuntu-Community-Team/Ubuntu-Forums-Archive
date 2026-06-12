---
title: "export x264 10-bit in ubuntu?"
date: 2014-10-08
forum: Ubuntu Studio
---

### Post by awithd on 2014-10-08
hai:lolflag:):P
how can i export video as x264 10bit not 8bit in ubuntu
because my out video is bad and not corect it's like this.
[IMG]https://lh4.googleusercontent.com/-alr04SwDtOo/VB7myWz8HrI/AAAAAAAAAAo/RBBt6-N0QXU/w916-h515-no/1.png[/IMG]
when i change the bitrate or quality in shotcut or pitivi or kdenlive or other editor movie i found that the result not change and the banding still in my output.
i found that ffmpeg and gstreamer not support 10 bit output.
this problem only with videos.:popcorn:
vlc and smplayer give good result . but other not.

---

### Post by andrew.46 on 2014-10-08
I suspect you might be asking the wrong question but x264 can certainly be configured for a bit depth of 10:

```

andrew@ilium~/source/x264/x264$**[COLOR="#FF0000"] ./configure --help | grep bit-depth[/COLOR]**
  --bit-depth=BIT_DEPTH    set output bit depth (8-10) [8]

```

You can see here that the *default* is 8....

---

