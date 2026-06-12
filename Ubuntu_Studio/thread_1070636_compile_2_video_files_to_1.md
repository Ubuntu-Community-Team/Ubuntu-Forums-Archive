---
title: "compile 2 video files to 1?"
date: 2009-02-15
forum: Ubuntu Studio
---

### Post by KanineN on 2009-02-15
Hello! I have a movie that is in 2 part, how do I compile them so they become 2 files. I hope you understand. I have mencoder and ffmpeg or do I have to install another program for this purpose?

---

### Post by Jose Catre-Vandis on 2009-02-15
> **KanineN said:**
> Hello! I have a movie that is in 2 part, how do I compile them so they become 2 files. I hope you understand. I have mencoder and ffmpeg or do I have to install another program for this purpose?

Assuming they are the same bitrate and resolution:
```
mencoder first.avi second.avi -oac copy -ovc copy -o output.avi
```

If in different formats you will have to convert first

---

### Post by itang sanjana on 2009-02-15
Or, you can run video editing for this purpose.
Try Kino or Cinelerra.
HTH

---

### Post by andrew.46 on 2009-02-16
Hi,

The FFmpeg FAQs speak of converting both files to mpg and then simply concatenating them. The example given is:
	

```
ffmpeg -i input1.avi -sameq intermediate1.mpg
ffmpeg -i input2.avi -sameq intermediate2.mpg
cat intermediate1.mpg intermediate2.mpg > intermediate_all.mpg
ffmpeg -i intermediate_all.mpg -sameq output.avi
```

Might be well worth a try if you already have FFmpeg installed?

Andrew

---

