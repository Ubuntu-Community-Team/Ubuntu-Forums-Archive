---
title: "Jack server microphone issue"
date: 2016-10-15
forum: Ubuntu Studio
---

### Post by rschanzenbacher on 2016-10-15
I use Simple Screen recorder to record my desktop but when i record only the left channel has audio because the microphone is mono. Is there any way for SSR or Jack to know the microphone is mono and not have the left channel have audio while the right is silent.

---

### Post by jejeman on 2016-10-22
I don't quite understand the question, but you can ether:
- record mono
- connect left output to both inputs to have same audio on both stereo channels.

---

### Post by MartyBuntu on 2016-10-24
...or demux the audio, run it through Audacity, have it redone with the left audio on both channels, then remux the audio back with the video.
I know it sounds tedious, but it will work.

---

