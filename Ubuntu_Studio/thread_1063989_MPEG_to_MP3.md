---
title: "MPEG to MP3"
date: 2009-02-08
forum: Ubuntu Studio
---

### Post by theozzlives on 2009-02-08
I want to extract the audio out of a MPEG to make a MP3 so I can listen to it in my car. How do I do it???

---

### Post by howefield on 2009-02-08
Try

```
ffmpeg -i input_file.mpg -f mp3 output_file.mp3
```

---

### Post by theozzlives on 2009-02-08
> **howefield said:**
> Try

```
ffmpeg -i input_file.mpg -f mp3 output_file.mp3
```

didn't work, just gave me a ">" prompt, will audacity do it?

nevermind, it works... thanks

---

### Post by lswest on 2009-02-08
try this:
```
mplayer -dumpaudio inputfile.mpg -dumpfile outputfile.mp3
```

*edit* never mind, seems you got the ffmpeg command working.

---

