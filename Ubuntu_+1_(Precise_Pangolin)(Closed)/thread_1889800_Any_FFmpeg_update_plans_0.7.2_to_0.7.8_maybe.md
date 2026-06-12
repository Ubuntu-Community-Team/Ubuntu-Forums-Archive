---
title: "Any FFmpeg update plans 0.7.2 to 0.7.8 maybe?"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by forcecore on 2011-12-02
Is there any update plans for FFmpeg? thanks. 0.7.8 would be good if backward compatiblity is needed. This release would be very useful for LTS.

If it is impossible to move from 0.7.2 to 0.7.8 then i would be grateful if there is answer.

I myself use FFmpeg mostly for HD video processing and for Gstreamer playback.

---

### Post by cariboo on 2011-12-02
I'd suggest you create a bug report on Launchpad, or ask your question on the [ubuntu-devel]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel") mailing list, as we can't answer your question here.

---

### Post by xebian on 2011-12-02
> **forcecore said:**
> Is there any update plans for FFmpeg? thanks. 0.7.8 would be good if backward compatiblity is needed. This release would be very useful for LTS.

If it is impossible to move from 0.7.2 to 0.7.8 then i would be grateful if there is answer.

I myself use FFmpeg mostly for HD video processing and for Gstreamer playback.

From what I understand this 'ffmpeg' package shares only in name the real ffmpeg.  It's now based off the libav* codes which I believe were forked off ffmpeg.

---

### Post by xebian on 2011-12-02
I think there is a 0.8.7 version already?

---

### Post by Jordanwb on 2011-12-03
I've noticed that the current build of ffmpeg can't do 10bit x264 so requesting a newer build (perhaps of ffmpeg-mt) would be beneficial.

---

### Post by andrew.46 on 2011-12-03
> **Jordanwb said:**
> I've noticed that the current build of ffmpeg can't do 10bit x264 so requesting a newer build (perhaps of ffmpeg-mt) would be beneficial.

The ability to output 10bit h.264 from FFmpeg actually depends on x264 being compiled with the *--bit-depth=10* option rather than FFmpeg being built in any special way. Might be best to build your own to achieve this?

---

