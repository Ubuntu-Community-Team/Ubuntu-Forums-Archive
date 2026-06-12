---
title: "[SOLVED] open office"
date: 2008-12-27
forum: Ubuntu Studio
---

### Post by DarinB on 2008-12-27
I'm using using ibex...open office 2.4 Presentation sound breaks up the sound is not continuous. i didn't have this problem in hardy? (i think) but am sure it worked in gutsy and feisty, but that was oo 2,3?? I can't find anything on the web on it.

---

### Post by linux_tech on 2008-12-27
Installing libasound can help resolve stuttering
```

sudo apt-get install libasound2

sudo apt-get install libasound2-plugins

```

pulseaudio is sometimes the cause of stuttering as well,
try stopping and restarting it
```
gksudo killall pulseaudio
gksudo pulseaudio
```

---

### Post by DarinB on 2008-12-31
thanks it worked i already had the libs so killing pulse audio did it.

---

