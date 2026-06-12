---
title: "Sound in Ubuntu? (Not a problem just a discussion)"
date: 2009-04-20
forum: The Cafe
---

### Post by mattgaunt on 2009-04-20
Heya everyone,

I'm currently on hardy heron (Old I know but need it for development purposes) but the sound is pretty dodgy in that it works but only one application can use it, the second application just stalls and eventually crashes when it can't get access to sound.

All I was wondering is if this is just me, or is it common, and if it is common then does Ubuntu have any ideas on making it a bit more reliable? I often keep my eye out on new versions of ubuntu to see if sound gets any special mention but never really does and I was wondering if this was because it's not an important factor at the moment or whether its the other communities that aren't gettin any breakthroughs for Ubuntu to take advantage of?

Anyway yeah just wondered if anyone had the low down on it :)

Cheers,
Matt

---

### Post by Bölvaður on 2009-04-20
hardy... that means you have a mix of Alsa and OSS. And the reason you cannot get sound is because OSS and Alsa cannot access the audio card at the same time. So you should be able to find some applications that work at the same time.

It has been fixed by beginning to use pulse or only alsa. It is still a little problem for few, but it's slowly fading away. You might not remember but when hardy was out there were many support questions about this, but now there isn't.

---

### Post by James_Lochhead on 2009-04-20
> **mattgaunt said:**
> Heya everyone,

I'm currently on hardy heron (Old I know but need it for development purposes) but the sound is pretty dodgy in that it works but only one application can use it, the second application just stalls and eventually crashes when it can't get access to sound.

All I was wondering is if this is just me, or is it common, and if it is common then does Ubuntu have any ideas on making it a bit more reliable? I often keep my eye out on new versions of ubuntu to see if sound gets any special mention but never really does and I was wondering if this was because it's not an important factor at the moment or whether its the other communities that aren't gettin any breakthroughs for Ubuntu to take advantage of?

Anyway yeah just wondered if anyone had the low down on it :)

Cheers,
Matt

Its the problem of hardware using funny drivers and non-standard features. Just make sure your computer has a reliable sound card before you buy it. :-D
I don't think there is going to be any miracle cure for it. As the market share of Linux rises I am sure manufacturers will take more notice.

I have to edit a line in my sound files manually because of a little sub-woofer in the bottom of my HP laptop...

---

### Post by mikewhatever on 2009-04-20
I've experienced the same problem with 8.04, but IMO, the sound is neither dodgy, nor unreliable because of that particular issue. I can't speak for Ubuntu developers, but think it safe to assume that had there been a fix, it would have been provided. Frustrating as it may sound, not everything has an easy fix.

> **Bölvaður said:**
> 
It has been fixed by beginning to use pulse or only alsa. It is still a little problem for few, but it's slowly fading away. You might not remember but when hardy was out there were many support questions about this, but now there isn't.

No it hasn't. In my case, pulseaudio was the cause of the problem.

> **James_Lochhead said:**
> Its the problem of hardware using funny drivers and non-standard features. Just make sure your computer has a reliable sound card before you buy it.

What's that supposed to mean?

---

### Post by mattgaunt on 2009-04-20
Well im on an apple macbook, purely because as much as I love Ubuntu it can let me down right when I need so needed a fail safe. But next desktop computer I put together I'll be sure to get some Ubuntu happy components.

Well hopefully when summer comes Ill be free of exams and can install Jaunty :-)

---

### Post by James_Lochhead on 2009-04-20
> **mikewhatever said:**
> What's that supposed to mean?

My little (useless) sub-woofer is what it means. :P

---

### Post by pwnst*r on 2009-04-20
> **James_Lochhead said:**
> My little (useless) sub-woofer is what it means. :P

what.

---

### Post by racerraul on 2009-04-20
I have noticed the same issues when paying music (via banshe or Rhythmbox) and browsing the web for videos...

I have to close the music program or I can't hear the video... if it plays at all...

---

### Post by RichardLinx on 2009-04-20
Wow, I completely forgot about that problem up until now (Haven't used Hardy Heron pretty much since a month after it's release). I'm pretty sure it was an issue with Pulse Audio.

You can probably fix it by just running:

```
sudo apt-get remove pulseaudio
```

And then: ```
sudo apt-get install esound
```

That should fix it. I remember discovering this while listening to music only to find that sound wouldn't play on a youtube video, and vice versa. This issue was fixed in 8.10.

---

