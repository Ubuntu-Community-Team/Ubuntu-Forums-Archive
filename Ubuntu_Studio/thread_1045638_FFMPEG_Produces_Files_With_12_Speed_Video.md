---
title: "FFMPEG Produces Files With 1/2 Speed Video"
date: 2009-01-20
forum: Ubuntu Studio
---

### Post by HalNineThousand on 2009-01-20
I just mentioned this in another thread, and thought maybe it should be a separate thread, both so the right people might see it and so it's easy for others to see it when searching for an answer.  I'm using this command line in ffmpeg:

ffmpeg -threads 2 -i /data/Data/Video/Dance/RawMTS/SweptAway-DeepRun.mts -deinterlace -r 29.97 -vcodec mpeg4 -s 704x384 -aspect 16:9 -b 4096kb -acodec libfaac -ab 512kb -ar 48000 -ac 2 /data/Data/Video/Dance/Testing/SweptAway-DeepRunX.mp4

It transcodes and produces video I can use, but when I play the file in VLC, the running time is listed as twice what it should be (3:14 in length becomes 6:27 in length).  The sound plays at normal speed, but the video is 1/2 speed.  As you'd expect, half way through, the sound ends as it should and the video is only 1/2 way through.

What do I need to do to produce video at normal speed so it and the sound are synced?

Thanks!

---

### Post by stefangr1 on 2009-01-20
I have no idea what this is caused by (your options look reasonable and I always use mencoder myself), but you might want to correct it afterwards as coding can take quite some time, which you can do using "MKV files creator".

---

### Post by HalNineThousand on 2009-01-20
Are you using Mencoder for transcoding .mts files?  If so, what does your command line look like?

---

### Post by stefangr1 on 2009-01-21
> **HalNineThousand said:**
> Are you using Mencoder for transcoding .mts files?  If so, what does your command line look like?

No, I never encoded mts files. I just googled arount a little, and it seems that there's indeed something strange going on. It seems like an old bug that has never been fixed, and that affects only the output produced by certain cameras.

You might be able to correct for it by using the -speed option, but I just tried for a few minutes on a sample file, and there seems not to be a clear logic behind it.

---

### Post by HalNineThousand on 2009-01-21
As best I could see by playing around, mencoder and MPlayer don't recognize mts files at all.

---

### Post by stefangr1 on 2009-01-22
> **HalNineThousand said:**
> As best I could see by playing around, mencoder and MPlayer don't recognize mts files at all.

They don't associate the .mts and .m2ts AVCHD format with mplayer. However, when you rename them to .ts or open them from the command line they will play. The sample file I downloaded yesterday also had a wrong video speed. When I reencoded it with mencoder, it said that the audio track lasted 8.# seconds and the video track 14.# seconds. However, when I then added an option like -speed 14.#/8.# that helped, but there was still a substantial difference. I think, however, there should be a single value that would do the trick, I just don't know what it is...

---

