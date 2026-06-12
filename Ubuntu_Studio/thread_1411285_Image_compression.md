---
title: "Image compression"
date: 2010-02-19
forum: Ubuntu Studio
---

### Post by mlhazan on 2010-02-19
Dear Experts,
Hope you guys are doing well.I have a Folder named "Photo".I that folder I have other folders each contains hundreds of jpeg images.All of them has taken by me using 10 mega pixel camera so the images have taken so much disk space.I need to know is there any software for linux which can convert them about 50% small without making them noisy.I know Gimp does it very well but for that I have to convert one by one which will take 5/8 days.

Any kind of help will be highly appreciated.

Sincerely,
ml

---

### Post by diesch on 2010-02-19
Have a look at phatch  (GUI) or ImageMagick (command line)

---

### Post by ron999 on 2010-02-19
> **diesch said:**
> ImageMagick (command line)
Yes, the command line instruction is like this:-
```
convert picture.jpg -resize 50% newpicture.jpg

```
So it would need a small script to process a whole folder.

---

### Post by lovinglinux on 2010-02-19
If you prefer a GUI, then use [Phatch](apt:phatch).

---

### Post by 23dornot23d on 2010-02-19
Leave them as they are and buy a cheap USB hard drive ...... 

put your new photos onto that ...... by copying them into a brand new folder on the USB hard drive ..... 

Never mess with the originals unless you have backups spmewhere ...... my advice and I take loads of photos ......

USB hard drive versus ..... loads of old photos changed ....... not worth it if anything should go wrong ....

or at least keep backups ........ on DVD Discs ...... 

But depends on if you have another reason why you need to compress ? other than disc space problems

---

