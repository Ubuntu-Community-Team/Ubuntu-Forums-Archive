---
title: "Cross platform encoding"
date: 2009-10-14
forum: Ubuntu Studio
---

### Post by G.W. on 2009-10-14
Hi,

I am looking to encode video (with ffmpeg/mencoder) to a format that will play on Linux, MacOS (Quicktime) and Windows (Media Player). I assumed the best format for this would be mpeg4 but I can't for the life of me encode it in a way that plays at least on Linux and Quicktime.

I haven't touched Windows since the year 2000 so I am not sure what kind of codecs it supports out of the box. If their codec support is still poor then I can't change that. But Quicktime should work,right?

Also as a kind of similar issue, does anyone know how to encode to a format that can be embedded in Powerpoint?

To recap:

- How to encode to mpeg4 or **any other format** that will play on Linux, Quicktime and if possible Windows Media Player?

- How to encode to a format that can be used with powerpoint?

I hope I could make myself clear and thank you very much for your help!

---

### Post by cotcot on 2009-10-14
I use .mpg in some powerpoints. Impress (Openooffice) performs better.

If you install the necessary codecs a lot of video formats are cross platform. 

There is a vlc version for windows that is able to read the video formats as you would use them in linux.

---

### Post by G.W. on 2009-10-14
Ok so powerpoint supports mpg, that is good to hear. Now I just need to know how to encode that. You do not happen to encode the mpg's you use yourself? If so, could you share the settings? Because I manage to create a couple of different mpeg4 files but none of them would play in windows... 
What kind of codec would I have to include with the video to make sure a windows user can play it?

I guess an mpg that would be usable in powerpoint would also be playable by quicktime. So if I can get that going that would solve my problem.

And thank you for your reply!

---

### Post by rylleman on 2009-10-14
I've spent quite some time to get this working and have a solution for Quicktime playable files here;
[http://rylanderanimation.se/2009/10/12/convert-to-quicktime-player-compliant-movs/]("http://rylanderanimation.se/2009/10/12/convert-to-quicktime-player-compliant-movs/")
It converts any movie to h264 movs at the same size as the input file. I do have a version of the script that resizes also and will add that to the current script.

---

### Post by G.W. on 2009-10-14
Hey, nice! I see we are in the same business. Thanks for the script, I'm on the road now but I will try it out when I get home... And I wanted to take a look at your showreel, but it's offline!? I'd really like to see that.

Cheers

---

### Post by rylleman on 2009-10-14
Hope you'll have use for the script. I'll upload the resize-version soon too.

I just refurnished my website and apparently misplaced that clip. Now it should work again. Thanks for pointing it out. It's a bit old but I'm working on a new reel right now.

---

### Post by rylleman on 2009-10-15
I've updated with that resizing version now.
Are you also in the animation business G.W.?

---

### Post by G.W. on 2009-10-19
So, I was able to encode the files to my satisfaction.

rylleman, thanks for the script. It works well for quicktime. I am doing technical visualization, originally coming from Maya and Shake/Aftereffects on Windows. I switched to Linux around 2000 and nowadays I am doing 90% of what I need in Linux. Actually I am looking forward to visiting the Blender Conference end of this week!

Concerning the encoding, a bit later I found a nice app called [traGtor]("http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/") where I found the following settings:

Windows mpg:
msmpeg4v2 and libmp3lame, container avi

wmv:
wmv2 and wmav2, container avi

quicktime:
mpeg4 and libfaac, container mov

If anyone has to add something I would be intrigued.

---

