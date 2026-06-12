---
title: "Encoding Xvid in Linux vs Windows. VERY slow using FFMPEG."
date: 2010-01-24
forum: Ubuntu Studio
---

### Post by MetalMusicAddict on 2010-01-24
I'm used to using Gordian Know with official XviD encoder in windows. Typically, I can do a 2-pass encoding in as long as the movie is long. But, using FFMPEG (self-compiled from SVN)under linux it takes twice as long. I have a dual-core system and I think I have the correct options enabled. (though it looks like the 2nd core isn't being used)

```
[SIZE="1"]ffmpeg -y -i "$a" -threads 2 -vcodec libxvid -aspect 2.35 -maxrate 1800kb -b 1500kb -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -croptop 140 -cropbottom 140 -s 640x272 -b 1800k -pass 1 -an -f avi /dev/null[/SIZE]
```
(keep in mind this is part of a script)

Any ideas?

---

### Post by FakeOutdoorsman on 2010-01-24
> **MetalMusicAddict said:**
> I'm used to using Gordian Know with official XviD encoder in windows. Typically, I can do a 2-pass encoding in as long as the movie is long. But, using FFMPEG (self-compiled from SVN)under linux it takes twice as long. I have a dual-core system and I think I have the correct options enabled. (though it looks like the 2nd core isn't being used)

```
[SIZE="1"]ffmpeg -y -i "$a" -threads 2 -vcodec libxvid -aspect 2.35 -maxrate 1800kb -b 1500kb -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv -trellis -aic -cmp 2 -subcmp 2 -g 300 -croptop 140 -cropbottom 140 -s 640x272 -b 1800k -pass 1 -an -f avi /dev/null[/SIZE]
```
(keep in mind this is part of a script)

Any ideas?

What version of Ubuntu are you using?
Can you show your complete FFmpeg output that you get after running your command?
Can you give some info on your CPU?  The *cat /proc/cpuinfo* command works well for that.

Keep in mind that your Windows program may be using a setting that chooses speed over quality.  It might be interesting to see what settings that program is using.  Might also be worth inspecting the output from GK with mediainfo.

Do you need to use libxvid?  You may be able to get a faster and higher quality encode with libx264.

---

### Post by no2498 on 2010-01-30
try tragtor or piviti

---

### Post by MetalMusicAddict on 2010-01-30
I appreciate the help but I'm trying to work with FFMPEG. The way I get to the result matters and I wanna get there with FFMPEG. ;)

---

### Post by andrew.46 on 2010-01-30
Hi MetalMusicAddict,

An interesting comparison might be to use FFmpeg's native version of 'xvid' rather than the external library you are currently using. For this simply use:

```
-vcodec mpeg4 -vtag XVID
```

instead of:

```
-vcodec libxvid 
```

All the best,

Andrew

---

### Post by MetalMusicAddict on 2010-02-07
I did give ***[SIZE="2"]-vcodec mpeg4 -vtag XVID[/SIZE]*** a go. I got a couple of FPS more but not much. is the MPEG-4 encoder threaded? I notice it (and libxvid) are only hitting one of my cores.

x264 is using both cores though. Odd.

---

### Post by li-on on 2010-02-14
Make sure you have yasm instaled before compiling xvid.

---

