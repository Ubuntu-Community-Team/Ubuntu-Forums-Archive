---
title: "How do I convert Wink SWF to FLV files for use in JW FLV Player?"
date: 2009-02-26
forum: Ubuntu Studio
---

### Post by tominglis on 2009-02-26
I have Kubuntu 8.04.2, and the Wink 1.5 (1060) software package from the repository.

I am using Wink to create animated / annotated / interactive screencasts for a website I am building.

The files are outputted as SWF files, which I believe are compressed with an proprietary Wink algorithm (it mentions on the Wink FAQ that the latest version supports uncompressed SWF but this may be referring to the Windows version, as I don't see an option for it).

I was wondering what the best way of converting these SWF files into FLV files for use with the JW FLV Player is? Can I use FFMPEG, and if so what is the command I should use?

---

### Post by FakeOutdoorsman on 2009-02-26
FFmpeg should be able to do this if it can decode the SWF from Wink.  Paste the output of:
```
ffmpeg -i input.swf
```
With *input.swf* being replaced by the name of your video of course.

---

