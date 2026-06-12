---
title: "A good screen recorder for games (mostly)."
date: 2020-05-05
forum: Ubuntu, Linux and OS Chat
---

### Post by Perfect Storm on 2020-05-05
Hello,

I'm playing around with KDE Neon at the moment. What I'm looking for is a good qt/KDE screen recorder that can record steam games.
Yes, I play games on Linux and recording it, like this: [https://youtu.be/p_f-HK7URMc](https://youtu.be/p_f-HK7URMc)


regards,

---

### Post by CatKiller on 2020-05-05
It's not something that I've ever done, but my understanding is that most people use OBS.

---

### Post by Shibblet on 2020-05-05
> **Artificial Intelligence said:**
> Hello,

I'm playing around with KDE Neon at the moment. What I'm looking for is a good qt/KDE screen recorder that can record steam games.
Yes, I play games on Linux and recording it, like this: [https://youtu.be/p_f-HK7URMc](https://youtu.be/p_f-HK7URMc)


regards,

On Windows, the driver utility (Geforce Experience, AMD ReLive, Intel Quick Sync) can turn on the hardware based screen capture encoding.

Are there no utilities that utilize the hardware encoding on Linux?

---

### Post by TheFu on 2020-05-05
i don't game, but have a few different ways to record video.

For stuff that doesn't require much CPU, i'll use **simplescreenrecorder**.  There's a PPA.

For stuff that does need all the CPU, there are external recorders that don't need any computer, just storage.  They cost from $60-$250. The cheaper ones cannot live-stream.  AGPTek is the brand i have. it sits between the computer and monitor and captures 1080i and stereo audio to directly attached USB storage (NTFS or FAT32 only).  After recording, connect the storage to any computer for post-processing.

i have used OBS to mux multiple video and audio inputs, but not under heavy CPU workloads.  Basically, i capture the sources however that is needed, then mux after-the-fact.

---

### Post by Perfect Storm on 2020-05-05
In elementary OS app center which have special designed apps, there's an app called **screencast** that are easy to use and can record heavy gaming.
I have tried OBS and other and they seems they can't cope or stutter performances.


regards,

---

### Post by Perfect Storm on 2020-05-05
> **Shibblet said:**
> On Windows, the driver utility (Geforce Experience, AMD ReLive, Intel Quick Sync) can turn on the hardware based screen capture encoding.

Are there no utilities that utilize the hardware encoding on Linux?

Not what I'm aware of. And it's surprise me that noone ever thought of making it.

---

### Post by CatKiller on 2020-05-05
> **Shibblet said:**
> On Windows, the driver utility (Geforce Experience, AMD ReLive, Intel Quick Sync) can turn on the hardware based screen capture encoding.

Are there no utilities that utilize the hardware encoding on Linux?

OBS (and simplescreenrecorder, I think) can use nvenc because ffmpeg can use nvenc. I don't know about the Intel & AMD solutions, but I don't see why they wouldn't work too.

---

### Post by wildmanne39 on 2020-05-05
Hello AI.

*Thread moved to **Ubuntu, Linux and OS Chat for a more appropriate fit**.*

---

### Post by mIk3_08 on 2020-05-06
I am not much fanatic in games but If you are gamer, Im sure you have a good system hardware specifications. I think it matters a lot. And in terms of desktop recording, I think and in my opinion OBS will do. Hope it helps.

---

### Post by TheFu on 2020-05-06
Googled "linux ffmpeg hw-based encoding" found this: [https://trac.ffmpeg.org/wiki/HWAccelIntro](https://trac.ffmpeg.org/wiki/HWAccelIntro) has a table of supported and non-supported capabilities.  Decoding video has been available on Intel, nVidia and AMD GPUs since about 2012.  HW-encoding for h.264 and h.265 not so much.  Apple has worse support than Linux.

I've not noticed that HW encoding to be automatic with any tools.  The last GPU I bought specifically has the capability, but I don't think it has ever been used.  The 12 threaded CPU + SW encoder in that machine has always seemed really fast compared to the 1st gen Core i7 it replaced.  Plus, it uses over 50% less Watts.

---

### Post by mastablasta on 2020-05-08
one more for simplescreenrecorder. though for games we only did a test on GOG game (F.E.A.R) installed in Play on linux. it worked perfectly. i then edited it on shotcut and posted it on youtube privately to be shared. 

OBS seems a bit overkill with the options. at least for me. i would use it if i did this professionally.

---

