---
title: "Streaming .ogg video on website"
date: 2009-07-03
forum: Ubuntu Studio
---

### Post by derekeverett on 2009-07-03
I would like to be able to stream some video on my website.

From the testing I have done it appears easy enough to do with quicktime but I would really like to try using .ogg if possible and reasonable. 

I have spent the past couple days googling and experimenting and nothing I have done seems to work quite right. I'm not finding any real clear information on converting different file types to ogg or how to stream them on the website.

Cortado appears to be the answer for streaming but I have yet to get it to actually work despite numerous attempts. It's possible that the .mpg was converted incorrectly. I need help! lol

Has anybody actually gotten something like this working?

---

### Post by raboofje on 2009-07-04
> **derekeverett said:**
> Cortado appears to be the answer for streaming but I have yet to get it to actually work despite numerous attempts.

Looks interesting - i tried [http://stream.fluendo.com/demosite](http://stream.fluendo.com/demosite) (video on demand, ogg, medium), and it fails to play the first clip. For the second clip, it shows the first frame, then java-6-sun crashes and takes firefox with it :S.

> It's possible that the .mpg was converted incorrectly.

Can you post it somewhere or is it private?

---

### Post by derekeverett on 2009-07-04
I've had a little progress since I posted. But not much..

I got cortado to work on the site.. but I still have 2 problems/concerns..

1) I can't seem to convert the video to .ogg without losing the audio.

2) When I watch the video a folder called "cache" appears on my desktop?!?

If you are interested in trying it yourself I can pm you the link but I can't post it here.. the forum won't let me.

---

### Post by raboofje on 2009-07-05
> **derekeverett said:**
> 1) I can't seem to convert the video to .ogg without losing the audio.

How did you convert it? mencoder?

---

### Post by derekeverett on 2009-07-05
No I ended up using ffmpeg2theora.

But if you are going to try it save yourself a big headache and follow this little tutorial that an Ubuntu forums staff member showed me

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

If you just download it from the normal repositories like I did you will likely have sound issues as I experienced.

The usage of the program is easy, at the command line:

```
ffmpeg2theora somefile.mpg
```

gives an output file of somefile.ogg

and it's 1/6 the original file size with great quality!!

---

