---
title: "Skype Video Upload Speed"
date: 2010-03-02
forum: System76 Support
---

### Post by vttay03 on 2010-03-02
Is there anyway to adjust the video resolution on the webcam found on the Starling netbook?  My video clarity is very high in Skype, however my movements seem choppy.  I'm not really sure where to start looking for this.  I don't seem to find any options within Skype itself so I was wondering if I could set them on the actual device.  Any help is appreciated...

---

### Post by thomasaaron on 2010-03-02
> Is there anyway to adjust the video resolution on the webcam found on the Starling netbook?

No.

```
My video clarity is very high in Skype, however my movements seem choppy.
```

You might try turning off everything BUT skype to see if that improves it.

---

### Post by vttay03 on 2010-03-03
> 
You might try turning off everything BUT skype to see if that improves it. 


Skype is the only application running if that's what you mean.  I searched around a bit and found a couple of promising leads but nothing seemed to make a significant difference.  My father is running Skype on a much lower speed internet connection and his video is not nearly as choppy as mine.  However, he's running it under Windows - it may just be a limitation in the Linux version of Skype.  The version I'm running does say it's a "Beta" version.

---

### Post by awilliams11964 on 2010-03-03
I just bought a Starling, down loaded SKYPE 32 bit, and the video and speakers work OK, but the built in microphone does not.
 
Any clues?

---

### Post by vttay03 on 2010-03-03
Fortunately, I didn't encounter microphone setup problems when I installed.  However, the following thread may offer some insight:

[http://ubuntuforums.org/showthread.php?t=1399448]("http://ubuntuforums.org/showthread.php?t=1399448")

---

### Post by thomasaaron on 2010-03-03
That newest version has, I believe, some issues with pulseaudio.

Try completely closing down skype and then running...

killall pulseaudio

...from a terminal.

Then open Skype, go to Skype's audio settings and see if you can get it to work. Let me know if that doesn't work, and I'll make some time to experiment with it and get some screenshots.

---

