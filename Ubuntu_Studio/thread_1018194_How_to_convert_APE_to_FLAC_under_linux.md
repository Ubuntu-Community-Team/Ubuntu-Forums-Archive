---
title: "How to convert APE to FLAC under linux"
date: 2008-12-21
forum: Ubuntu Studio
---

### Post by Kejing on 2008-12-21
Install wine and download monkey audio application from its official site and install in wine.

Use the monkey audio to decompress the APE file. Then use 'flac' to compress WAV file. 

I don't know how to use shntool and don't want to learn too much CLI script, so use the graphic way plus some command.

---

### Post by FakeOutdoorsman on 2008-12-22
Using ffmpeg:
```
ffmpeg -i inputaudio.ape outputaudio.flac
```

---

