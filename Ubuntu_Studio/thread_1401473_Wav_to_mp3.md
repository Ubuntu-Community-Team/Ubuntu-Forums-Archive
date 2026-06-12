---
title: "Wav to mp3"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by Mogor on 2010-02-08
I am to sad (( How to convert wav to mp3?
Is thats a right section to ask this question?

---

### Post by cascade9 on 2010-02-08
The easiest way is with soundconverter (gtk) or soundkonverter (KDE)

---

### Post by x33a on 2010-02-08
There are multiple software available for audio conversion. some good ones are:
rubyripper, soundjuicer, even mencoder or vlc can do the job.

---

### Post by saif_held on 2010-02-15
I use VLC for most of the conversion issues. I find it great and simple.

---

### Post by Chronon on 2010-02-15
> **Mogor said:**
> What about commercial converters like this one for example - <snip>  ?
Are they better than free converters?

That looks like snake oil to me.  I would expect such a product to contain malware, honestly.

---

### Post by Jose Catre-Vandis on 2010-02-15
ffmpeg will do this nicely from the command line, and you can script to deal with batches:

```
 ffmpeg -i input.wav output.mp3
```

You can add further options for sample rate, bitrate and encoder if you wish

---

