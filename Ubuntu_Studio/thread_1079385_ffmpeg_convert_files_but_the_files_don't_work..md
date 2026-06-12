---
title: "ffmpeg convert files but the files don't work."
date: 2009-02-24
forum: Ubuntu Studio
---

### Post by KanineN on 2009-02-24
Hello! I have converted files for a good while now with ffmpeg but now it have just stopped and the files doesn't play on my mobile.

the line i'm using is

```
ffmpeg -i INPUT -r 25 -f mp4 -vcodec mpeg4 -ar 48000 -b 500k  -ab 128k -y OUTPUT
```

note that i'm doing this with fuocoTools. 

I get this in the terminal. 

[http://sv.tinypic.com/view.php?pic=6nv4p0&s=5](http://sv.tinypic.com/view.php?pic=6nv4p0&s=5)

---

### Post by Shampyon on 2009-02-27
I don't know much about converting videos from the command line, but I do know that some phones are pretty picky about the settings of the videos. Some will only play videos with certain audio/video bitrates, framerates and dimensions. My Moto V3i would only accept three or four different bitrate and sample rate settings, and only in 3GP format.

The first thing I'd do is check the manufacturer's specifications for media files.

---

### Post by andrew.46 on 2009-02-27
Hi KanineN,

> **KanineN said:**
> Hello! I have converted files for a good while now with ffmpeg but now it have just stopped and the files doesn't play on my mobile.

Can you play this file on your computer? Looks like the encode is going along ok with a few error messages that *probably* could be ignored. BTW you can post images to the forums themselves rather than the 3rd party site you have used. Have a look at 'Additional Options ---> Attach Files' below the area where you type your message.

Andrew

---

### Post by KanineN on 2009-03-08
First of all I would like to say sorry becuase of the inactivity I had. But because of the studies I havn't got any time for this.

@andrew.46 The movie is playing but after a while it seems like the movie gets a error and stops. becuase of the computer that I'm having I can't watch movies so well. Yes, this computer sucks!

---

