---
title: "PAL to NTSC conversion via ffmpeg--why is output file much larger than input?"
date: 2008-06-16
forum: Ubuntu Studio
---

### Post by pytheas22 on 2008-06-16
I have a DVD made for viewing in PAL zones, and I'm trying to make a copy that can be played on NTSC equipment.  I extracted all of the video and combined it into one 4.3 gigabyte file.  The file uses mpeg-2 and AC-3 compression and is in PAL resolution.

ffmpeg converts the video to NTSC resolution well.  The problem is that the output file I get is 6.8 gigabytes, more than one-and-a-half times the size of the original file.  I want to fit everything on one DVD, so this is causing a problem.  I don't understand why the output file is so much larger than the input file, since I'm using the same compression scheme for the video.  Am I doing something wrong?  Below is the ffmpeg command that I used:

```
ffmpeg -i /home/chris/Desktop/Schönbrunn\ Vienna\ 2006/VIDEO_TS/all.VOB -f avi -vcodec mpeg2 -b 800 -g 300 -bf 2 -acodec copy -target ntsc-dvd -ab 128 /home/chris/Desktop/rieu/movie.avi
```

Thanks for any suggestions on how to get the output down to ~4.3 gigabytes.

---

### Post by eye208 on 2008-06-17
```
mencoder /home/chris/Desktop/Schönbrunn\ Vienna\ 2006/VIDEO_TS/all.VOB -vf scale=720:480,harddup -ovc lavc -oac copy -of mpeg -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=5000:keyint=15:vstrict=0:aspect=16/9 -mpegopts format=dvd:tsaf:tele_src=25:tele_dest=30000/1001 -o /home/chris/Desktop/rieu/movie.mpg
```
This is for a typical PAL DVD movie (25fps progressive content, not telecined). The tele_src/tele_dest parameters will flag the frames for 25->29.97fps soft telecine to make the stream NTSC-compliant without changing the actual frame rate. Since NTSC frames are smaller than PAL frames, the resulting file may even turn out smaller than the original.

---

### Post by Terry of Astoria on 2008-06-17
How did you originally get your vob file? 

I have the same problem to solve. A PAL DVD - and I want to convert to NTSC for a friend. She bought the movie "Walker" on ebay without realizing it's incompatible with her player. I was trying a weird workaround where I would dvd:rip it to xvid and then use mplayer or something to make a NTSC DVD. I've made a few DVD's from avis and such. One of the programs I used was mkdvd.pike but it isn't supported anymore and doesn't work out of the box in Ubuntu because of dependency issues. I ripped the movie and it's OK but I'd like to do what was suggested above with mencoder for better quality results. However I am not knowledgeable enough to know how to extract the video and other data and make that VOB file. How ought I approach that task?

---

### Post by eye208 on 2008-06-17
You can use vobcopy to copy the VOBs to your harddisc. If libdvdcss is installed it will automatically be used for decryption.

---

### Post by pytheas22 on 2008-06-17
Thanks to eye208 for that command.  It worked much better than the one I was trying, but unfortunately the file is still too large--it came out to 5.8 gigabytes.  Is there anything I could do to make it smaller?  Would reducing the vbitrate number help?

I'm not quite sure how I got the VOB files, as I made them during my first attempt at this project six months ago.  I got frustrated then and haven't found time to give it a second shot until now.  I think that the only software I used at that time was dvd:rip and tovid, so I imagine I pulled the video off of the PAL DVD using dvd:rip, if that's possible.  Or it might have been vobcopy or something similar; I don't remember.  I got lots of small VOB files for each chapter of the DVD, and I piped them together with > to make one big file, because I wanted to simplify things and don't care too much whether the DVD is broken down into chapters.  I know that I was able to burn a DVD then using tovid, but it wouldn't play on my DVD player because the screen resolution was still PAL.

Anyway, I'm currently giving Kino a shot to see if it will give me a more reasonably sized output file and will post my results.

---

### Post by eye208 on 2008-06-17
> **pytheas22 said:**
> Would reducing the vbitrate number help?
Yes, it should help. DVDs have an upper bitrate limit, but you can always go lower.

---

### Post by pytheas22 on 2008-06-17
With a video bitrate of 2500, the file came out to just over 3 gigabytes.  The quality was decent enough so I just went with that instead of trying to figure out what the highest value would be that would keep the size below 4.4 gigabytes.  It burned fine with DVD Styler, and plays on my DVD player.  So Terry of Astoria, I'd recommend using the command that eye208 gave above; it should convert the video to NTSC and preserve the quality.

Thanks for the help in figuring this out.

---

