---
title: "Timestretching (timeshifting) in video players"
date: 2006-07-14
forum: The Cafe
---

### Post by lutzky on 2006-07-14
Timestretching is changing the length of an audio stream without changing the pitch. This is used in Windows Media Player, for example, to be able to 'speed up' or 'slow down' video. In my university (the Technion), we have access to recorded videos of the lectures for most courses, and we find it useful to be able to view them, for example, at 1.4x the original speed. (This saves much time, and they stay intelligible)

In linux, what I gather about the situation is this:

- There is a library called libsoundtouch, which timestretches audio very efficiently. There is at least one audio player which allows easily changing speed (while preserving pitch) during playback with little to no overhead.

- In mplayer, you can speed/slow the video (using the [] keys), but pitch is not preserved (a.k.a chipmunk mode). mplayer is my favorite player, and the optimal solution for me would be that [] would work the same, but would preserve pitch using libsoundtouch.

- In xine, changing the video speed disables audio altogether. (Audio will only play at original speed)

- Mythtv seems to support libsoundtouch fully - however, it isn't a particularily good (from what I've seen) general-purpose video player, and doesn't handle wmv files well (crashes on seek)

- Using gxine, you can get access to a plugin which does timestretching. However, the interface is extremely annoying to use, and the plugin does not use libsoundtouch, and has poor audio quality.

Any suggestions?

---

