---
title: "IMG formats .gif .jpg .png"
date: 2008-11-16
forum: The Cafe
---

### Post by kevdog on 2008-11-16
Way back in the early 1990's, .gif used to be the format of choice.  It was a lossless format using a variant of the LZW compression algorithm, however could only preserve 8 bits/pixel and was proprietary owned by Compuserve.   Is Compuserve around anymore? Is the .gif patent expired?  If not, who currently holds the patent?

.gif went on to be replaced by .jpg. I believe .jpg is open source and could handle up to 32 bits/pixel however was a lossless format whereby image quality was inversely proportional to file size.

.png is a newer format, is a lossless format, can handle 32 bits/pixel (I think?), and can preserve transparency information.  It seems in my experience this format has really never penetrated the mass market (ie camera's etc).  Is this format proprietary also?  Also I don't truly understand the quality factor.  For example if you specify a quality of 95 -- the 9 variable represents the compression level 0-9 (0=no compression, 9=maximum compression) and 5 represents some filter quality which I dont understand (Possible values 0-5).  Can someone explain this to me?

---

### Post by ssam on 2008-11-16
GIF patents are expired
[http://en.wikipedia.org/wiki/GIF#Unisys_and_LZW_patent_enforcement](http://en.wikipedia.org/wiki/GIF#Unisys_and_LZW_patent_enforcement)
still common for logos (which have few colours), or small animations.

JPEG is lossy, that is you cannot recover the exact original image. however the algorithm is very good at getting rid of information that you cant see. it is good at doing smooth gradients. You can get a factor of 5 or 10 compression with very little visible loss, especially on photos.

PNG is lossless (you can exactly recover the original). it can handle high colour depth and alpha channels. it is better than jpeg for logos and things with flat colours as it gives no compression artefacts. no need to use png on photos as the file size will be large.

---

### Post by saulgoode on 2008-11-16
> **kevdog said:**
> Also I don't truly understand the quality factor.  For example if you specify a quality of 95 -- the 9 variable represents the compression level 0-9 (0=no compression, 9=maximum compression) and 5 represents some filter quality which I dont understand (Possible values 0-5).  Can someone explain this to me?

PNG is a lossless format regardless of compression level. The only effect compression has is on the amount of space the file occupies and the time it takes to transfer the file. Unless you have a particular reason otherwise[1], I would recommend always using a PNG compression level of "9".


[1] One possible reason for not compressing your file is to speed up saving to and loading from disk (in highly intensive I/O settings such as  very large images or editing video as a sequence of PNG images). Even in this case, it is possible that, with modern processors, the time saved by using smaller compressed files is greater than that lost by having to (de)compress them.

---

### Post by kevdog on 2008-11-16
Although I know it would depend on the actual image itself, how do file sizes with png compression 9 compare to 85 quality of jpeg?

---

### Post by miggols99 on 2008-11-16
Compare the two images. The first one is JPG, the second PNG.

---

