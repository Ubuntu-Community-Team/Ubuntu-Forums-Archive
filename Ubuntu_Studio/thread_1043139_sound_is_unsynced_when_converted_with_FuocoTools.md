---
title: "sound is unsynced when converted with FuocoTools"
date: 2009-01-18
forum: Ubuntu Studio
---

### Post by KanineN on 2009-01-18
Hello! When I am converting a .flv file to a .mp4 the sound gets unsynced. 


I use the code 

```
ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 700k -ab 192k -y OUTPUT
```


Is there any chance to fix it?

---

### Post by FakeOutdoorsman on 2009-01-19
What is the full output of ffmpeg when you try your command?  Does it unsync if you try the command without "-r 25"?

---

