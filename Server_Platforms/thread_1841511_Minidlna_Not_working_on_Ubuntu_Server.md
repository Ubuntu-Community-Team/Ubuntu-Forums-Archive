---
title: "Minidlna Not working on Ubuntu Server"
date: 2011-09-09
forum: Server Platforms
---

### Post by sloopjonb on 2011-09-09
Hi,

I'm having some problems with my 1st Ubuntu server configuration. I've got a HP Microserver which I hope to use minidlna and samba on to provide storage for my home PC, and serve up videos to our Xbox.

I installed minidlna yesterday and all was working fine - I was able to browse the minidlna shared folder and play a video. I shut the machine down, and today when I came to give the machine its final test before deploying I find that I can no longer get the minidlna server to serve anything up :confused: I'm trying to browse the DLNA content using VLC (same thing that worked yesterday) - today absolutely nothing works.

Beginning to tear my hair out.....

Any suggestions for what to try would be much appreciated.

Cheers, Jon

---

### Post by wolfbuddy on 2011-09-09
Is minidlna starting up when the server boots? Sounds like it isn't.

---

### Post by CharlesA on 2011-09-09
Moved the post to it's own thread.

Is minidlna running? Check with ps aux | grep or sudo netstat -nlp

---

