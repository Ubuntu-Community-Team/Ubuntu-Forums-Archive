---
title: "Wine Opens Multiple Instances Of Same Game..Normal?"
date: 2009-01-24
forum: Wine
---

### Post by axlekitty on 2009-01-24
Title says all. Basically I am trying to run WoW with wine. All works fine till about 10-15 mins into game. I used htop when I first started WoW and it had only 1 instance of the .exe. After 10-15 mins (the point it slows to a crawl) there are around 10 or so instances of WoW open. Is this normal to see with wine? If not is there a way to make it only be able to open one? I don't click it more than once so it's not that. I thought this to be initially an ati driver issue but I'm not so sure now.  :(

Latest Wine
Latest Ubuntu

---

### Post by cogadh on 2009-01-24
I'm afraid I don't have a solution for you, but I can tell you that is not normal Wine behavior.

---

### Post by axlekitty on 2009-01-24
Thanks for letting me know, hoping someone can pop in here to help that knows what's up. Not running regular window manager though, using xfce I think it's called, if that info helps, probably not, lol.

edited to ad.

The instances of wow do not show when I try to alt-tab them. Only one is visible. Just there are many many wow.exe processes open in the htop window.

---

### Post by hikaricore on 2009-01-24
Actually this is normal, well it shouldn't slow down... but you're seeing what we call "threads".

These are most common on multicore systems where the game is "threaded" into different pids to lighten the workload of a single processor core, but I have seen this on single core cpus as well.  Each and every thread is actually the same program.  Imagine cutting a sandwich into 4 pieces to fit on smaller plates.  It doesn't suddenly become 4 brand new sandwiches just because it's been split.

Wow that was a lame analogy.

How fast is your CPU and how much RAM do you have?
Also please tell us your video hardware/what drivers you're using for it and if you are running desktop effects or not.

---

### Post by axlekitty on 2009-01-24
2.8ghz processor with 2g ram. shouldn't be seeing this slowdown with those specs though. wow is rated at like 1.8ghz 512 ram.

---

### Post by hikaricore on 2009-01-24
Video hardware?

---

### Post by axlekitty on 2009-01-24
0 desktop effects

x800 pro 256mb vidram

ati 8.12 drivers
Originally thought it was the old video card driver memory leak they used to have in the old drivers (supposedly fixed) recurring (still might be...)

edit:
I have enabled the wine registry hacks and every setting recommended. Works at full fps for 10-15 mins.

---

