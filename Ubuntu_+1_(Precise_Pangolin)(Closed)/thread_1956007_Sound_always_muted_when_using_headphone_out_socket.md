---
title: "Sound always muted when using headphone out socket"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sonicb00m on 2012-04-10
I often connect my laptop to an amplifier via the headphone socket or use my headphones to listen to music.

However, Ubuntu is detecting that headphones are inserted and then muting the Speaker output in the alsa mixer, which is really annoying.

How do I stop it doing this every time I reboot as it seems to be purposely turning itself off.

---

### Post by sonicb00m on 2012-04-10
I made a temporary fix adding

amixer set "Speaker" unmute 100% > /dev/null

to the bottom of .bashrc and it seems to work.

---

### Post by sonicb00m on 2012-04-11
Oh that didn't help my problem because the speaker is muted when the headphones are inserted. Not when the computer is rebooted.

There must be a script somewhere turning the speaker off. How do I find it?

---

