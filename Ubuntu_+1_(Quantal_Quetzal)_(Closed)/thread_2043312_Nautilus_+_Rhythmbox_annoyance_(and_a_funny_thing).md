---
title: "Nautilus + Rhythmbox annoyance (and a funny thing)"
date: 2012-08-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by effenberg0x0 on 2012-08-16
When I double-click a wav/ogg file in Nautilus, the media plays normally. If I dounle-click a second media file, it also plays normally, but then my entire music playslist starts playing right after. I found out about it as I was checking for another bug (Thunderbird mail notifications, which I'm posting here in a second).

To test:
- Make sure Rhythbox is set as your default media player
- Kill all rhythbox instances. As in $killall rhythmbox
- Open a Semi-Nautilus window and navigate to a directory with some sounds files. I have tested with /usr/share/sounds/gnome/default/alerts
- Double-click a file. I have tested with "bark.ogg". The sound will play normally.
- Now double-click another file. I have tested with drip.ogg. The sound will also play and, if you have a playlist set at Rhythmbox, it will start your playlist.  

At this point, if you wanna continue testing with individual sound files you might have, you have to either open Rhythmbox GUI and stop the playlist or kill it again.

Now the funny story: This thing above started as I was looking for notification sounds to be played when email arrives on Thunderbird (which actually doesn't work, see my other post). I had just woke up. I clicked "glass.ogg" and didn't really hear the glass sound cause it's brief and volume was sort of low. Instead I heard a piano tune. 

After 10 seconds I though "hey, what a long notification sound...Ubuntu is really changing... but, ok, the piano is good".

Then at 25 seconds I thought "wtf, Ubuntu people went mad?". I looked at my mug. "Did someone put something in my coffee?"

Then I realized rhythmbox was playing this unusual playlist. 

Now please see this media to understand why this was funny:
[http://www.youtube.com/watch?v=tOOtiI7yCaE](http://www.youtube.com/watch?v=tOOtiI7yCaE)

Regards,
Effenberg

---

### Post by dino99 on 2012-08-16
Pure supposition:

if you add (by default) each played sound to the playing list, then rythmbox continue with that list

---

### Post by effenberg0x0 on 2012-08-16
> **dino99 said:**
> Pure supposition:

if you add (by default) each played sound to the playing list, then rythmbox continue with that list

I believe you're right. I think there's no way to change this config in Rhythmbox (couldn't find it). And if semi-nautilus will use the default media player to play/preview any sound file (instead of directly playing it via media libs or invoking a console media player), testing/previewing individual sound files, without starting any playlist, is currently impossible.

It's not the end of the world but it is an annoying limitation.

Regards,
Effenberg

---

