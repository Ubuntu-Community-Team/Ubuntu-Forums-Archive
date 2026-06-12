---
title: "Encode video for Palm Centro?"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by stevejesus on 2008-10-02
Hi all,

My wife and I both bought the Palm Centro last night from Sprint and we are amazed.  I set up synching on both of our laptops (8.04) with no issues.  She is hook on address book, memo and calender syncing through Evolution.

Only issue now is Video.  We both have the Kinoma player, which as I understand will play everything, but no way to encode video specifically for our screen format and resolution.  Any ideas?  I tried to run Kinoma's "producer" in wine with no luck.

---

### Post by aeiah on 2008-10-02
does it come with a demo video or anything? if so, just check what that's encoded at and use those settings. if not, you'll have to do some digging on google or experimenting i guess

---

### Post by stevejesus on 2008-10-03
We switched to TCPMP as our player.  We transcode using mencoder, and all video plays fine.  
One problem.  When I encode a 16:9 video, it distorts itself to 4:3...  I need to find a way to make a letterboxed video so that there is no distortion.  This is what I am doing;

```
mencoder -vf scale=320:240 -oac mp3lame -lameopts mode=0:cbr:br=96  -af volnorm -srate 32000 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=250  input.avi -o output.avi
```

How do I handle different aspect ratios?  I tried cropping, but that didn't work.  Is there a way I can have mencoder do this automatically?

---

### Post by stevejesus on 2008-10-03
Also the video is out of sync.  Does that have anything to do with mencoder?

---

