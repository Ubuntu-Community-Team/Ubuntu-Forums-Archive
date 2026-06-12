---
title: "How can I make a PDF type document of just jpg pictures?"
date: 2009-03-06
forum: Ubuntu Studio
---

### Post by DavidRichy on 2009-03-06
I have about 180 jpg pictures that I want to view as one continuous document. I tried doing this with OpenOffice, but seeing that each picture is 3.1 mbs, this would take a very, very long time, and I have a very slow computer. Is there a program or just a quicker way to do this?

---

### Post by kaibob on 2009-03-06
You can do this with the Imagemagick convert utility. Just open a terminal window, change to the directory that contains the JPG files, and enter:

```
convert *.jpg -adjoin filename.pdf
```

Imagemagick is not installed by default but is in the repo's. Convert options that can be used to reduce size and make other changes are explained at:

[http://www.imagemagick.org/script/convert.php](http://www.imagemagick.org/script/convert.php)

---

### Post by DavidRichy on 2009-03-07
I tried ```
convert *.JPG -adjoin filename.pdf
```, but I get the following error: ```
convert *.JPG -adjoin filename.pdf Killed.
```

Am I doing something wrong?

---

### Post by kaibob on 2009-03-07
I've never run into that message, so I did a google search on the words, imagemagick convert killed. It appears that the killed message most commonly results from memory limitations. Given the size of your JPG images and the number of images being processed, a problem with memory is not surprising. 

The only suggestion I can make is to first downsize the images then try again to join them. To resize, it's probably best to do this with the mogrify command:

[http://www.imagemagick.org/script/mogrify.php](http://www.imagemagick.org/script/mogrify.php)

Mogrify overwrites the input files, so be sure you work with backups and not the originals.

BTW, I assume that the JPG extension of your files are capitalized. I'm sure you know that linux file names are  case sensitive, but I noticed you're new to the forum (and perhaps to linux).

---

### Post by DavidRichy on 2009-03-07
You were right. The files were too big so I used ```
mogrify -resize 440 * .JPG
``` to make them the right size (I guess pdf documents can not be larger than 30 mb's or above 640 resolution), and then I used ```
convert *.JPG -adjoin filename.pdf
``` to make the pdf document, which worked, and yeah, I'm new to linux, this is only one of the tons of walls I've hit into, or this is the only wall that's been solved for me :), 
thanks for your help.

---

