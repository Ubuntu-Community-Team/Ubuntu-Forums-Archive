---
title: "FFmpeg Can't create jpeg thumbnails in Intrepid"
date: 2009-01-30
forum: Ubuntu Studio
---

### Post by pt123 on 2009-01-30
n Hardy using the medibuntu packages one was able to create thumbnails from an xvid file

ffmpeg -i "testfile.avi" -r .01 -y ~/ss_%d_yy.jpg

now this doesn't work on Intrepid using the unstripped ffmpeg libraries in Intrepid because medibuntu doesn't provide ffmpeg versions

but png files work
ffmpeg -i "testfile.avi" -r .01 -y ~/ss_%d_yy.png

I prefer jpg to png as the filesizes are much smaller.

Am I doing something wrong, or is this the way it i:(

---

### Post by FakeOutdoorsman on 2009-01-30
Works fine for me using ffmpeg in Intrepid from the repository without the unstripped libraries:
```
ffmpeg -i input.avi output%d.jpg
```
What errors does ffmpeg give with your original command?  What are you trying to achieve with "-r .01"?

---

### Post by pt123 on 2009-01-30
r is so you don't end up trashing your hard disk
it takes thumbnails at every frames per second

so 0.1 would give around 40 thumbnails for a 40 minute video than the million your command would do.

---

