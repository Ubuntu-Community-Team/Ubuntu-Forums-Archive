---
title: "live feed from screen"
date: 2008-06-01
forum: Ubuntu Studio
---

### Post by ipburbank on 2008-06-01
I am using stickam (stickam.com) to broadcast live video from my webcam. I am wondering if there is a program that will make my desktop show up as a USB camera. So a screen casting program, but it needs to be live. I have a quad core, overclocked to 3.5 GHZ, and a good graphics card so speed isn't an issue. But it does need to work with 8.04, and I noticed that some don't yet. Thanks for any help, Istvan.

---

### Post by ipburbank on 2008-07-21
guys? anybody? does vlc do this?

---

### Post by ipburbank on 2008-08-12
SOLVED! If you use recordmydesktop and encode on the fly it in effect 'streams' to the destination folder, and from there you can use VLC or another tool to stream the video.

---

### Post by Chocomochino on 2008-08-25
yeah, but you are using a lot of space, i mean, if you stay 10 minutes using this, or 1 hour it will take up space, isn't there another solution?

---

### Post by ipburbank on 2008-08-25
i'm hoping so too, there are many faults in this approach. for example when the feed is played it starts from the beggining, so there will be a delay:( help? anyone?

---

### Post by ipburbank on 2008-10-25
anyone? please?

---

### Post by Lars Noodén on 2008-10-26
This is just a shot in the dark.

How about if instead of saving to a file, you save to a named pipe?
   [http://linux.die.net/man/1/mkfifo](http://linux.die.net/man/1/mkfifo)

Then your broadcast reads from the pipe.  

The disk (should) never fill.  But on the downside, you don't keep a recorded copy automatically this way.

---

### Post by ipburbank on 2008-11-09
anyone know of a program?

---

### Post by ipburbank on 2008-11-09
I found webcam studio, but that seems to deffinatly be in beta, because All i get is a black screen.

---

### Post by duffrecords on 2008-11-09
Maybe [xwinwrap]("http://swik.net/xwinwrap") might work; it replaces the desktop with a movie or screensaver.  Normally you would use xwinwrap with mplayer to play a video file but instead of specifying a file, try using /dev/video0 instead (or whatever device your webcam is).  Linux interprets everything, including hardware, as files and folders so I imagine it should work.  For instance, I can pipe my TV tuner card straight into mplayer like this:```
cat /dev/video0 | mplayer -
```

---

