---
title: "Is Ther A Program To Delay Audio Files For A Few Seconds?"
date: 2010-11-21
forum: The Cafe
---

### Post by giddyup306 on 2010-11-21
I've been trying to find a way for the past half an hour with no luck.  I need it to delay a track with the vocals cut out so I have enough time to go from the computer to my guitar so I can play along with it.  All I could find on Goggle were people that were having problems with audio delay.

Thanks.

---

### Post by Austin25 on 2010-11-21
Well, you could use audacity and add a few seconds of blank space at the start. I'm sure there's also a solution involving JACK.

---

### Post by giddyup306 on 2010-11-21
> **Austin25 said:**
> Well, you could use audacity and add a few seconds of blank space at the start. I'm sure there's also a solution involving JACK.


Thanks dude, found what I was looking for.  I tried finding ways in Totem and VLC, but this was just too obvious. lol

---

### Post by wewantutopia on 2010-11-21
You can record a track of a few seconds of silence.  Then add it as the first track in a playlist including the song you want to accompany you.  That way you don't have to add silence to every song you ever want to play along with.

---

### Post by Warpnow on 2010-11-22
In the Terminal

sleep #;command


So, like, 

sleep 15;totem song.mp3

It would sleep for 15 seconds then make totem open the file song.mp3

---

