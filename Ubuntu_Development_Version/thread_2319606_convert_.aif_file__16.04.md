---
title: "convert *.aif file | 16.04"
date: 2016-04-05
forum: Ubuntu Development Version
---

### Post by mikeincousa on 2016-04-05
I have a series of *.aif / Mac audio files that I would like to put into an Ubuntu friendly format.
Ideally I would like a no-fuss / virtual no-brainer solution.

[[COLOR=#1155cc][FONT=Georgia][/FONT][/COLOR]]("http://askubuntu.com/questions/286535/how-to-convert-aif-audio-files-to-mp3")[COLOR=#1155cc]_[http://askubuntu.com/questions/286535/how-to-convert-aif-audio-files-to-mp3](http://askubuntu.com/questions/286535/how-to-convert-aif-audio-files-to-mp3)_[/COLOR]
This looked promising, but I tried installing a couple and did not succeed.
Most notably, 
FF-Multi Converter: which seemed to be the best bet with clear install commands
…....
E: Package 'ffmulticonverter' has no installation candidate.

As I do not use Linux much these days, I am wondering if the above links have grown old, or if I am missing something, or if my woes spring from a new release bug of some sort.

Any solutions, especially simplistic ones, will be appreciated.

---

### Post by Bucky Ball on 2016-04-05
Tried Soundconverter? It's in the repositories (Software Centre).

---

### Post by gordintoronto on 2016-04-06
I hope you realize that 16.04 has not been released yet, it's a beta -- so you might encounter bugs.

---

### Post by Bucky Ball on 2016-04-06
> **gordintoronto said:**
> I hope you realize that 16.04 has not been released yet, it's a beta -- so you might encounter bugs.

*Thread moved to **Ubuntu Development Version**.*

---

### Post by Rustan on 2016-04-06
[https://www.howtoforge.com/tutorial/ffmpeg-audio-conversion/](https://www.howtoforge.com/tutorial/ffmpeg-audio-conversion/)

```
[COLOR=#000000][FONT=&amp]*sudo apt-get install ffmpeg*[/FONT][/COLOR]
```

```
[COLOR=#000000][FONT=&amp]*ffmpeg -i "filename.aif" "newfilename.flac"*[/FONT][/COLOR]
```

....

---

