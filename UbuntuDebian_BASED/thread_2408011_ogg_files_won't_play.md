---
title: "ogg files won't play"
date: 2018-12-12
forum: Ubuntu/Debian BASED
---

### Post by frank105 on 2018-12-12
Hmm...

I ripped a bunch of my cd's several years ago and put them on an external HD.  Now - plugged the HD in and try and play the files - and nothing.  Tried it in VLC and also Clementine.  Randomly I ripped some of the CD's in MP3 and they all work.  

The .ogg files have size and are not 0kb or anything. 

What next?  What should I do to start troubleshooting?

BTW - Tested on my laptop in MX linux.  Tested on wife's laptop in Peppermint.  

Thanks in advance for any ideas.

---

### Post by TheFu on 2018-12-12
A few ideas.  Don't know if any will work.

Rip one again using ogg and see if it works or not.  Could be that the ogg/vorbis libraries just aren't installed?

Use the '**file**' command to see if the headers provide any useful info.
I would try **mpv** an **mplayer** as well. **VLC** should play almost anything, provided it isn't a *snap* install.

Do you have an ubuntu machine to test with?

---

### Post by vanadium on 2018-12-12
Symptoms of not playing? Error message? Apparently playing with duration displayed, but no sound? You may try to open one of these files in Audacity audio editor.

---

### Post by frank105 on 2018-12-12
Ooohhh... Some good ideas.  I will get you some info from those tests.  

But - btw - the pc I ripped the .ogg's on does not exist anymore.  So ripping them with the new laptop would probably not give much intel?  (Or did I miss it.)  

Thanks,

---

### Post by howefield on 2018-12-12
Thread moved to the "*Ubuntu/Debian BASED*" forum.

Try playing one from the terminal to get some clue.. eg

```
cvlc path/to/file
```

---

