---
title: "ffmpeg with audio ripping from .flv issues with current ubuntu release."
date: 2009-08-18
forum: Ubuntu Studio
---

### Post by Dave_Connor on 2009-08-18
The current version in Ubuntu works fine with ffmpeg but recently stopped working with .flv files and not reconizing the video encoding. I compiled the latest version from ffmpeg.org and it works fine but apt-get wants to upgrade me back to the non-working version of ffmpeg. Is there a later release I could upgrade to so I would not need to worry about this issue ?

---

### Post by andrew.46 on 2009-08-19
Hi Dave,

> **Dave_Connor said:**
> I compiled the latest version from ffmpeg.org and it works fine but apt-get wants to upgrade me back to the non-working version of ffmpeg. Is there a later release I could upgrade to so I would not need to worry about this issue ?

Your best bet might be to use the Fakeoutdoorsman's guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

This guide produces a current copy of FFmpeg that integrates neatly with the Ubuntu package management system.

Andrew

---

### Post by Dave_Connor on 2009-08-19
Thanks :) I now knew that was issues with ffmpeg was with the package version that apt-get was checking and wanted to replace. Thanks for the guide it is working correctly and working fine with .flv files now. The linux community really helps you out when you need it :)

---

### Post by andrew.46 on 2009-08-19
Hi Dave,

> **Dave_Connor said:**
> Thanks :) I now knew that was issues with ffmpeg was with the package version that apt-get was checking and wanted to replace. Thanks for the guide it is working correctly and working fine with .flv files now. The linux community really helps you out when you need it :)

Great news! We all owe a debt to the Fakeoutdoorsman, myself in particular as it was that very guide that introduced me to FFmpeg :-).

Andrew

---

