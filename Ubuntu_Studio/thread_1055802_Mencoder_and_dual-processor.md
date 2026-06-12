---
title: "Mencoder and dual-processor"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by sbrbot on 2009-01-31
I do have a dual core CPU on my notebook. Mencoder uses only one of them while encoding (I see that CPU usage is 50% all the time).

:KS Is there any mains to force mencoder to use both CPU cores for encoding?

---

### Post by Ng Oon-Ee on 2009-01-31
Well, I use ffmpeg instead of mencoder, and what you have to do with ffmpeg is to recompile from source with different compile flags (--cpu=core2 in ffmpeg's case).

Why not search the net for mencoder compilation from source and see what you turn up? May not be for you if you're brand-new to all this though. If you'd like a look at the ffmpeg compile-from-source guide I followed, [check out FakeOutdoorsman's great guide here.]("http://ubuntuforums.org/showthread.php?t=786095") Not sure if he's already included some additional things I suggested in the replies though, but the guide itself is terrific!

---

### Post by andrew.46 on 2009-01-31
Hi sbrbot,

> **sbrbot said:**
> I do have a dual core CPU on my notebook. Mencoder uses only one of them while encoding (I see that CPU usage is 50% all the time).

:KS Is there any mains to force mencoder to use both CPU cores for encoding?

If you are using h264 encoding there is an option:

> 
       threads=<0-16>
              Spawn threads to encode in parallel on multiple CPUs (default: 1).
              This  has  a  slight  penalty to compression quality.  0 or 'auto'
              tells x264 to detect how many CPUs you have and pick an  appropri-
              ate number of threads.



Is this what you had in mind? I am not sure about different encoders as I will admit to turning more to FFmpeg these days :p.

Andrew

---

### Post by sbrbot on 2009-01-31
My primary goal is to backup my kids' original cartoon DVDs by encoding them into DivX and to reproduce them on standalone DVD (with DivX support) player. You can imagine how kids treat DVDs.

For example, I encoded my cartoons into Xvid with these parameters:

```
mencoder dvd://1 -alang hr -oac mp3lame -lameopts vbr=3 -ovc xvid -xvidencopts bitrate=1000:cartoon:vhq=1 -o CARTOON.avi
```

Only one pass took 215 minutes for about 81 minutes of movie on 2.5GHz CPU (actually my CPU is dual core 2x2.5GHz but mencoder uses only one of cores during encoding process). (lavc only needs 18 minutes for this one pass encoding).

I'll see how to compile mencoder on my own in order to enable dual core support.

However, I'm not sure if my standalone DVD player supports x264 but probably not.

---

### Post by nowardev on 2009-01-31
i have made a gui for mencoder ffmpeg and ffmpeg2theora 

anyway 

this is the option 

-ovc xvid -xvidencopts bitrate=900:threads=2

threads=2 

means dual core if you have more ... :D change it

---

