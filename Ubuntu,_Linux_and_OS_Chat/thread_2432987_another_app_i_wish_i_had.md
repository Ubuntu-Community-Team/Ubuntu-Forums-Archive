---
title: "another app i wish i had"
date: 2019-12-11
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-11
i wish i had an app that can compare two images and give me a probability the two images are the same.  i would expect a lossless format converted from a different lossless format would yield 1.000000 or 100%.  lossy conversions of the same size might get really close.  two different photos of the same thing should still be a high value.  comparing different sizes would be a bit more like comparing fuzzy images.  it should also detect crops and other variations like some editing.

*edit*:

i want this to be a command or python3 module so i can do some heavy-duty scripting around it.

---

### Post by sdsurfer on 2019-12-12
Sounds like a fun project . . . my first thought would be to integrate ImageMagick as it has tons of filters and options that may identify the characteristics of one image against another.

---

### Post by sudodus on 2019-12-12
There are tools using pattern recognition, a kind of artificial intelligence technology, that can do it. I have no link right now, but I think suitable FOSS tools can be found via the internet.

---

### Post by Skaperen on 2019-12-12
pattern recognition would be the way to get more accurate evaluations.  i don't know any AI programming methods.  good programming needs good understanding of what the project is about.  the best i could do is reduce the image sizes to match and guess based on how close the colors are in their 3D color space.  improvements could include increment resizing and sliding one image  around inside the other.  but that would add huge CPU increases.

---

### Post by sdsurfer on 2019-12-13
[https://imagemagick.org/script/compare.php](https://imagemagick.org/script/compare.php)

> Use the compare program to mathematically and visually annotate the difference between an image and its reconstruction.

---

### Post by Skaperen on 2019-12-13
my current goal is to cross compare some 20000 image files i have to look for duplicates.  i've already done this for exact duplicate files.  but there are still many duplicates in one form of difference or another.  all those in raw or raw-like formats (such as PBM) have been converted to PNG format to reduce space used, where i can.  i still need to figure out how best to store HDR in PNG.  i am hoping this can bunch apparently "identical" images together in a common directory where i can look them over and decide what to delete, what to keep, and what to convert.

i don't understand what the contents at that link is really saying.  all i really need is a reasonable probability of what it is the same as so i can bunch together those that "seem" to be the same or might be derived from another (like B is a crop of A).

---

### Post by bernard010 on 2019-12-13
I do believe that your talking about logarithms and anti-logarithms comprised with optical data. Which starts with completely different photos then gradually change to barely noticeable difference in photos. Which is a comparison image selection process with pre stored images for comparison to select the correct parameters for selecting the the image that is needed. With images certain points that have commonalities to select the correct one. is often a shortcut of sort as long as the required image is obtained. Ubuntu is the OS to accomplish this. Good Luck Programming. Hope you well. 
[h=1][/h]

---

### Post by Skaperen on 2019-12-14
i have no idea how logarithms would apply here.  if it is to get a linear intensity value, then that can make sense.  but what needs to be done, next?  scaling the image to a small size?

if i take a photo of a red flower in a yellow background and take another photo of a different red flower on a yellow background, i won't be surprised they are considered the same.  that would be rare.  but if all 20000 is a collection of red flowers all taken with a yellow background, then things can get difficult.

---

