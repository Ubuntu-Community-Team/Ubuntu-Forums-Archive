---
title: "Mencoder underutilizes CPU (transcoding)"
date: 2011-11-30
forum: Server Platforms
---

### Post by ffixcollector on 2011-11-30
I'm running PS3MediaServer and mencoder uses 280%-320% out of 400% CPU. I would like to transcode 1080p, but it just doesn't cut it. I have an Intel SE7520BD2 Server Motherboard w/Dual Xeon 2.8GHz CPUs, 1GB RAM

I ran a Handbrake encode, and it maxed out at 400%, so I do not believe that it is an Intel architecture issue

---

### Post by ian dobson on 2011-11-30
Hi, 

Looks as if memcoder is programmed to use so many threads in a very efficient way. 

I know that handbrake uses as many threads as possible (Handbrake on my 8way box uses 700-760% cpu) but the efficiency drops the more threads it uses (8 threads isn't double so quick as 4 threads).

Regards
Ian Dobson

---

### Post by ffixcollector on 2011-11-30
So your saying, there is nothing I can do?

---

### Post by arrrghhh on 2011-11-30
> **ffixcollector said:**
> So your saying, there is nothing I can do?

Increase the number of threads mencoder is using if possible.  Never needed to try, transcoding 1080p works just fine for me.

---

### Post by SeijiSensei on 2011-11-30
You can add threads=n to the options for lavc (-lavcopts) and x264 (-x264encopts). See the [man page](http://manpages.ubuntu.com/manpages/maverick/en/man1/mencoder.1.html) for details.

---

### Post by ffixcollector on 2011-11-30
I changed:
```
    mencoder test.mkv -ovc lavc -lavcopts vcodec=mpeg4:vhq:vbitrate=3000:aspect=4/3:threads=4:vpass=1 -vf pp=lb -oac mp3lame -lameopts vbr=3 -o test.avi
```
to threads=6, threads=8, threads=2, and threads=1. Still cant get above 75%

---

### Post by ffixcollector on 2011-12-03
SOLVED!

The Intel SE7520BD2 Server Motherboard has several options under the Processor tab that need to be set depending on desired performance... whatever that means. Anyways, enabling both allowed mencoder to better utilize the CPU. Thought its not 100%, it good enough to trancode 1080p :D

---

### Post by stmiller on 2011-12-03
ffmpeg is very multi-threaded friendly for an alternative

---

