---
title: "script for recording screencasts with ffmpeg (video+audio)"
date: 2009-06-02
forum: Ubuntu Studio
---

### Post by igorzwx on 2009-06-02
Dear friends,

I created a script for recording screencasts on Ubuntu 9.04.
I believe it might be useful.

It works well. The quality is good.
The screencasts can be published without any editing or noise removal.

Using the script, an ordinary user can easily produce a good
screencast with minimal efforts.
No expensive hardware is required.

The script is here:
[http://n2.nabble.com/new-version-of-the-script-for-recording-screencasts-%28video%2Baudio%29-on-Ubuntu-9.04-td3011916.html#a3011916](http://n2.nabble.com/new-version-of-the-script-for-recording-screencasts-%28video%2Baudio%29-on-Ubuntu-9.04-td3011916.html#a3011916)

Screenshots + howto are here:
[http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-td2988982.html#a2988982](http://n2.nabble.com/How-to-record-sound-on-Ubuntu-8.04%2C-8.10%2C-9.04-td2988982.html#a2988982)

One may need these screenshots to understand how to capture audio with ffmpeg

The script works on Ubuntu 9.04
It runs two ffmpegs, one capture screen, another records audio.
Then avi file (video+audio) is created.
This version of the script includes filtering and normalization (SoX
with Ladspa plugs).

One can also run the script on Ubuntu 8.04, or 8.10, but
this would require recompilation of ffmpeg.
See:
HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

To be fair, I am completely ignorant in shell scripting.
I just re-used somebody's script.
Therefore, I would be happy to hear any advice about how to improve the script.

Best regards,
[COLOR=#888888]Igor[/COLOR]

---

