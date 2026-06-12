---
title: "[SOLVED] Convert left-only stereo to both channel stereo or mono?"
date: 2008-09-26
forum: Ubuntu Studio
---

### Post by Statik on 2008-09-26
Hi all,

I am working on a video project that is almost done, using Blender's sequencer to produce some slide cross-fade's with PIP overlays. Everything is working great except for one problem. I used a wireless mic on the camcorder to get the interview audio and the audio is left channel only. I cannot seem to find a way to render it in both channels.

I have tried using Blender's FFMPEG with the -ac 1 option. I've tried using AVIDeMux on the output file to render down to mono. I've tried loading it in Kino and KDenLive, all to no avail. I've even duplicated the tracks in blender and panned them left and right to get it centered, No luck.

Any suggestions?

Statik

---

### Post by rsambuca on 2008-09-26
Load the track in audacity.

---

### Post by Statik on 2008-09-27
And then mix it back in as another audio . . . I'll try that.

Statik

---

### Post by Statik on 2008-09-27
Audacity didn't work, but I did find a way to do it. I ended up using mplayer on the video to extract the audio as a mono WAV file that I could import into Blender as the audio file. They were rendered back out as a centered stereo track that sounds great. As soon as I'm done tweaking it I'll Vimeo it or something if you are all interested.

```
mplayer -vc null -vo null -ao pcm -af channels=1 -benchmark test.avi
```

Statik

---

