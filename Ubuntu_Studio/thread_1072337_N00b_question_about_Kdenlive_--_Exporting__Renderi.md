---
title: "N00b question about Kdenlive -- Exporting / Rendering"
date: 2009-02-17
forum: Ubuntu Studio
---

### Post by eagle_one on 2009-02-17
a new Kdenlive user here... i need to cut off the last few seconds of an MPG file and then save the file in the same MPG format. here's my problem -- i've already setup, copied to a new track and cut out the necessary section of the MPG. when i go to export / render timeline i'm required to re-encode the file. i don't want to re-encode the file... all i want to do is cut off the last few seconds and then save the file in it's original MPG format. is this possible? many thanks.

---

### Post by cotcot on 2009-02-17
Have not checked it with kdenlive.
With avidemux it is possible without re-encoding.

---

### Post by eagle_one on 2009-02-17
thanks -- i'll check out avidemux... btw are there any special tricks for cutting off the last few seconds / cropping MPGs in avidemux?

re my original post above, it appears there is no way to avoid re-encoding with Kdenlive although this may be a feature in the future:

[http://www.kdenlive.org/forum/lossless-no-reencoding](http://www.kdenlive.org/forum/lossless-no-reencoding)

---

### Post by cotcot on 2009-02-20
> **eagle_one said:**
> thanks -- i'll check out avidemux... btw are there any special tricks for cutting off the last few seconds / cropping MPGs in avidemux?

re my original post above, it appears there is no way to avoid re-encoding with Kdenlive although this may be a feature in the future:

[http://www.kdenlive.org/forum/lossless-no-reencoding](http://www.kdenlive.org/forum/lossless-no-reencoding)

As said I do not have enough experience with kdenlive on this.
With avidemux you can cut of whatever part of the clip using the A and B setting to indicate the start frame and end frame of the part you want to cut out without re-encoding.

---

### Post by ouija on 2009-02-25
Yes, as far as I know kdenlive requires you to render and therefore process the data, where as avidemux can simply cut and remux the portion of the file you want, saving ample amounts of time.

---

