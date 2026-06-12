---
title: "Ardour and MP3's"
date: 2012-06-24
forum: Ubuntu Studio
---

### Post by MrBalloonHands on 2012-06-24
So I know you can't import an MP3 in to Ardour, but is there a work around? The reason I'm asking is my band mates gave me an MP3 file with a couple of instruments that they want me to put a bass line to the song. 

My whole intention was to record to the song, and combine them together in Audacity. 

Any suggestions or ideas are greatly appreciated.

---

### Post by jejeman on 2012-06-24
Convert it to wav.
For example
```
ffmpeg -i file.mp3 file.wav
```

---

### Post by MrBalloonHands on 2012-06-24
That did the trick. Thanks again man for the help. I found that avconv works well too. Same syntax. 
[B]
[/B]

---

### Post by sgx on 2012-06-25
audacity audio editor uses the many ladspa fx, so bass boost, low and
high pass filters, several EQ, and dozens more, are there for any
highlited selected audio, or portion, then export in the desired format and bit rate.

Cheers

---

