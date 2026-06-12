---
title: "mencoder only using one CPU"
date: 2009-11-03
forum: Ubuntu Studio
---

### Post by daniel_summers on 2009-11-03
I noticed that mencoder is only using one CPU core when compressing XviD video with MP3 audio.  I've searched, but I haven't been able to find a way to have it use both cores.  Is there a switch I could provide on the command-line to do it?  Here's the command I'm using...

```
mencoder dvd:// -vf scale=854:480 -alang en -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts pass=1 -ofps 24000/1001 -o /dev/null
mencoder dvd:// -vf scale=854:480 -alang en -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts pass=2:bitrate=-617000 -ofps 24000/1001 -o output.avi
```

---

### Post by disturbed1 on 2009-11-04
To -xvidencopts add threads=2. It will read like this 

[I]
mencoder dvd:// -vf scale=854:480 -alang en -oac mp3lame -lameopts abr:br=128 -ovc xvid -xvidencopts pass=2:bitrate=-617000**:threads=2** -ofps 24000/1001 -o output.avi[/I]

Don't expect a huge speed up. Xvid threaded encoding is not that efficient. If you have more than one video to encode, you're better off running two separate jobs at the same time. While you're gauging the speed increase, keep an eye on the encoding fps printed by mencoder, not total CPU usage. If you increase the number of threads too high, you'll end up core and cache thrashing. This will up the CPU usage, but degrade the encoding speeding (fps).

And is there a reason you are resizing to a resolution larger than the original? DVD resolution is 720x480. If it's 16:9, that's 720:384, 2.35:1 is 720:304. You can also use scale=720:-11 to retain aspect rounded to mod 16. If the original is 2.35 you can get the crop values with *mplayer dvd:// -vf cropdetect* this prints out the exact values you need.

---

### Post by daniel_summers on 2009-11-05
> **disturbed1 said:**
> To -xvidencopts add threads=2....

Don't expect a huge speed up. Xvid threaded encoding is not that efficient. If you have more than one video to encode, you're better off running two separate jobs at the same time. While you're gauging the speed increase, keep an eye on the encoding fps printed by mencoder, not total CPU usage. If you increase the number of threads too high, you'll end up core and cache thrashing. This will up the CPU usage, but degrade the encoding speeding (fps).

Thanks.  I just thought it was weird that it had 1 pegged, and the other was bored.  I'll give that a shot and see how the performance is.

> **disturbed1 said:**
> And is there a reason you are resizing to a resolution larger than the original? DVD resolution is 720x480. If it's 16:9, that's 720:384, 2.35:1 is 720:304. You can also use scale=720:-11 to retain aspect rounded to mod 16. If the original is 2.35 you can get the crop values with *mplayer dvd:// -vf cropdetect* this prints out the exact values you need.

That's the way the guide I read when I first started doing this said to do it.  It was a multi-step process of "-vf cropdetect" to get the crop values (for this particular example, it gave 720:480:0:0, so I just left crop off), then running "-vf crop=[values]" to get the scaling.  mplayer seems to scale up; most anamorphic seem to come in around 854x352.  Then, I put the whole thing together to get what you saw above.

I tried it once without the scale parameter, and the output wasn't good.  I'll have to give that 720:-11 thing a try; that sounds interesting.

Thanks so much for the information!

---

