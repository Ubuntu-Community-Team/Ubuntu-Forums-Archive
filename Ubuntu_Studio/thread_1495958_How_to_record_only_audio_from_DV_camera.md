---
title: "How to record only audio from DV camera"
date: 2010-05-28
forum: Ubuntu Studio
---

### Post by Xanmar on 2010-05-28
I've been messing around with Kino, and Audacity (as well as some Windows programs), and I haven't been able to figure out how to ONLY capture the audio from a camera directly plugged in to the computer (DV). I don't have enough tape to record all of the audio I need, so I just want it sent straight to my computer without me having to rip it from the video (due to low space on the hard drive). Does anybody know of a way to accomplish this?

---

### Post by pastalavista on 2010-05-28
Have you tried just playing it with Totem or whatever and using gnome-sound-recorder in the Applications->Sound & Video menu?.. or Audacity, since you've installed it already, to record while Totem is playing.

ps.. you could also try installing WinFF from the repositories. It should be able to convert it from the camera and save to disk.

---

### Post by Xanmar on 2010-05-28
Oh, no, I'm talking about a live capture, so I can completely bypass using the DV tapes, but only capturing the audio, and not the video.

---

### Post by pastalavista on 2010-05-28
> **Xanmar said:**
> Oh, no, I'm talking about a live capture, so I can completely bypass using the DV tapes, but only capturing the audio, and not the video.

Ah, I see. What kind of outputs are on the camera and inputs on the PC?

---

### Post by Xanmar on 2010-05-28
That's very strange... I've gotten it to work somehow. I bypassed the whole DV thing, and just plugged a dual-ended 3.5mm jack from the headphone input on the camera to the microphone input on the motherboard of my computer. The funny thing was, I tried that, and it didn't work. The only thing different that I did was go into System-Preferences-Sound, and click on the "Input" tab. After I did this, I realized that it suddenly started working in Audacity. Weird.

Anyways, thanks for the help.

---

