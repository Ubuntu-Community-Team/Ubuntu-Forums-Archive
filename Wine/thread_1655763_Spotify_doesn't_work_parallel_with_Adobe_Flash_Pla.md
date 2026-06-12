---
title: "Spotify doesn't work parallel with Adobe Flash Player"
date: 2010-12-30
forum: Wine
---

### Post by Godspell on 2010-12-30
Hello all,

I've googled this issue several times and found nothing useful so decided to start a new thread. I'm sorry if this results as yet another duplicate though.

Right, the problem I'm having is inconsistency with Spotify and unavailability of parallel running with Adobe Flash Player i.e. I can't pause the music and get on Firefox to watch YouTube video.

I followed all the instructions from Spotify web page and it works alright. But it CANNOT play the songs for long. It freezes after about  15 or 20 min and I have to restart Spotify. This happens all the time.

Another problem is as I mentioned above; if I watch YouTube videos while playing Spotify, they don't have any sound.
If I play music on Spotify whilst I'm on YouTube video (be that paused or even at the end of the clip), Spotify will generate an error msg:
> There is a problem with your sound card. Spotify can't play music.It's very annoying. Today's computing is all about multi-tasking, isn't it? I wouldn't necessarily watch a clip and listen to music at the same time but sometimes when you find a YouTube link or something, you'd pause Spotify and go on it and it's not possible in my case :S

So please anyone, if you have any idea how to resolve this issue, help me out here. I'm seconds away from smashing my monitor lol

Thank you very much.

Regards,
GS

EDIT: I use Ubuntu 10.04 64bit and Wine 1.2

---

### Post by Godspell on 2011-01-10
MASSIVE BUMP

Does nobody have this issue?

Please help me out here if you know any sort of solution.

---

### Post by Godspell on 2011-01-15
bump

---

### Post by cogadh on 2011-01-15
The problem is probably your sound card. It likely isn't a full hardware sound card and therefore can only process a single "stream" at a time. In Windows, this wouldn't be a problem as the sound card drivers can handle multiple streams, but in Linux, its not so easy. In the past, you could configure dmixer in ALSA to handle the streams, but now that Ubuntu is on Pulse, I'm not sure that would work.

---

### Post by Godspell on 2011-01-15
Double post due to serverside (proxy no response) problem.

---

### Post by Godspell on 2011-01-15
> **cogadh said:**
> The problem is probably your sound card. It likely isn't a full hardware sound card and therefore can only process a single "stream" at a time. In Windows, this wouldn't be a problem as the sound card drivers can handle multiple streams, but in Linux, its not so easy. In the past, you could configure dmixer in ALSA to handle the streams, but now that Ubuntu is on Pulse, I'm not sure that would work.

Right, I see. Thanks for the information.

I didn't know Pulse is new audio control. I thought ALSA was the recent one.

Well, in this case, this problem isn't just about Spotify anymore.

I can't use the headphone and mic correctly, either.

When the headphone is plugged in, the audio play both from it and  the laptop speakers.

Annoying as hell, really.

I have also searched this issue one Google but nothing useful.

Really pissed off and bummed :S

Regards,
GS

---

