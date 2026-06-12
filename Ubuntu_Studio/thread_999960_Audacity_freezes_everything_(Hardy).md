---
title: "Audacity freezes everything (Hardy)"
date: 2008-12-02
forum: Ubuntu Studio
---

### Post by lazylew on 2008-12-02
when exporting a wav-file in Audacity as an mp3, everything freezes after about 1 minute and 20 or 30 seconds

ctrl alt esc doesn't work - mouse doesn't move - even when keeping terminal open on purpose to kill Audacity when this occurs, I can't use the terminal cause of the freezing

I have to do a cold start every time - any idea what might be wrong?

---

### Post by Frihet on 2009-09-20
> **lazylew said:**
> when exporting a wav-file in Audacity as an mp3, everything freezes after about 1 minute and 20 or 30 seconds

ctrl alt esc doesn't work - mouse doesn't move - even when keeping terminal open on purpose to kill Audacity when this occurs, I can't use the terminal cause of the freezing

I have to do a cold start every time - any idea what might be wrong?

I am having a similar problem, and looking around the web, it is clear that something is wrong. In my case, Audacity (1.3.7) simply locks up randomly in the middle of an edit session. I have tried several rebuilds on two machines and get the same results. [edit -- I added the force quit button to my Gnome menu bar just for Audacity.] For now, I am editing under Windows XP, which works nicely.

---

### Post by lazylew on 2009-09-22
> **Frihet said:**
> I am having a similar problem, ... [edit -- I added the force quit button to my Gnome menu bar just for Audacity.] ...

My Audacity problem was solved long ago, but I have no clue how this came to be.
I also put the force quit on the panel and it will stay there forever :-)

---

### Post by sonicb00m on 2009-10-09
audacity does the same for me. doesn't matter what installation or configuration of ubuntu i use.

---

### Post by crazy ivan on 2009-12-21
Yeah... Audacity behaves strangely, even on Karmic Koala. But I found a nice hack today.
When working with audacity I like to have a shell open, where I can enter

```

killall audacity

```

But sometimes it doesn't freeze completely, but asks wether I would like to save the project.. I did, and now every time I open the project, audacity freezes instantaneously. Was afraid I lost all my audio, but I 
1) opened the .aup file with a text editor
2) changed the header to

```

h="0" zoom="1"

```

Now I can at least work with the files again.

---

### Post by suniyo on 2009-12-21
it is no different with me but in my case it doesn't work at all. i have a lot ram so it doesnt freezes but also doesn't encode files. it just doesn't do anything. Strange !!

---

### Post by Groucho Marxist on 2009-12-22
> **lazylew said:**
> when exporting a wav-file in Audacity as an mp3, everything freezes after about 1 minute and 20 or 30 seconds

ctrl alt esc doesn't work - mouse doesn't move - even when keeping terminal open on purpose to kill Audacity when this occurs, I can't use the terminal cause of the freezing

I have to do a cold start every time - any idea what might be wrong?

First of all, what type of computer are you using? Concurrently, how fast is your processor or processors? Are you multitasking at the same time, i.e. watching video/ streaming video while compressing the WAV to MP3?

---

### Post by Rob St. John on 2010-01-02
I have used Audacity on a Ubuntu 8.10, 9.04, and now on 9.10.  Audacity has worked fine on 8.10 and 9.04....AFTER struggling with pulse audio issues and no audio capture.  Thanks to to the forum for the assistance in getting pulse and audio capture working.

I have two boxes, both with AMD64, one with 1GB RAM and Ubuntu 9.10 and one with 512 RAM and Ubuntu 9.04.  I really like using Audacity for audio capture.  However, I also am experiencing the same Audacity freeze up on the 9.10 box.  It formerly worked fine with 9.04 Ubuntu Studio.  I have gone through a couple of fresh installs to see if that would help.  It will work fine for approximately 40 minutes of audio capture of web streamed audio either by Amarok, VLC, or the player initiated by a Shoutcast station.  I am not running any other applications.  

When it freezes up only the mouse moves, but clicking on anything doesn't work.  Nor does attempting to change to another display to log in.  killall or anything else isn't really an option because with the sysem frozen I haven't been able to access anything else.  The only option I have found is a cold reboot, yeeesshh.

I have wondered if I somehow had exceeded a "quota" for storing temporary files, but no quotas are in place and I have 164 GB of disk space.  I have wondered if it is a Pulse audio-Audacity tussle.  And I have wondered that since this box has a lot of peripherals and networked if there was some sort of interrupt conflict that was generated when one of the peripherals gets polled.  A search for solutions led me to this thread.  Thanks, Rob

---

### Post by lazylew on 2010-01-02
> **Groucho Marxist said:**
> First of all, what type of computer are you using? Concurrently, how fast is your processor or processors? Are you multitasking at the same time, i.e. watching video/ streaming video while compressing the WAV to MP3?
The issue I had was solved long ago (see post nr 3), but inexplicably.
Meanwhile I'm on a different pc without any problems in Audacity (touching wood...)

---

