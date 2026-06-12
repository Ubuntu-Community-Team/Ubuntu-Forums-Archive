---
title: "Need help with picture batch resizing script"
date: 2010-09-18
forum: The Cafe
---

### Post by RaZe42 on 2010-09-18
Okay, so here's a background:

I'm a hobbyist photographer, and I use Bibble 5 as my RAW converter on Linux.

I've found that using a step resizing method helps retain sharpness in web-sized images: 

See here for more details: [http://www.fredmiranda.com/forum/topic/726816](http://www.fredmiranda.com/forum/topic/726816) and [http://www.birdphotographers.net/forums/showthread.php?13989-Resize-Sharpen-for-Web](http://www.birdphotographers.net/forums/showthread.php?13989-Resize-Sharpen-for-Web)

The batch output queue in Bibble can call any program/command/script for each image.
The only thing the script has to do is scale the image down in let's say 5% steps and maybe apply light sharpening between every step.

I'm wondering how I should do this. With Imagemagick's command line utilities? With GIMP's odd little scripting thingie(seems unnecessarily complex)

---

### Post by Rasa1111 on 2010-09-18
I dont know how to do it using a script..
 But have you checked out "Phatch"? [http://photobatch.stani.be/](http://photobatch.stani.be/)
Really not positive if its even what youd need, or could use, 
But I saw the thread on it the other day and remembered it. 

 The creator is a member on these forums also.

Sorry if it is of no use to you. <3

---

### Post by RaZe42 on 2010-09-19
Phatch seems to be able to do this. But unfortunately it won't work(program runs but btach always fails). The problem seems to be an api change in pyexiv2(which was in May). Phatch hasn't been updated to the new api. Maybe the project is dead?

---

### Post by lykeion on 2010-09-19
Resize to 95% using ImageMagick:
```
convert <original_image> -resize 95% <resized_image>
```

Sharpen using ImageMagick:
```
convert <original_image> -sharpen <radius>x<sigma> <sharpened_image>
```<radius> is an integer value from 0 to 3
<sigma> is a floating point value from .1 to 3.0
start with radius 0 and experiment with the more significant sigma value in the area of .5 to 1.0
There is also unsharp mask, see 
[http://www.imagemagick.org/script/command-line-options.php#unsharp](http://www.imagemagick.org/script/command-line-options.php#unsharp)

Reference:
[http://www.imagemagick.org/script/command-line-options.php#resize](http://www.imagemagick.org/script/command-line-options.php#resize)
[http://www.imagemagick.org/script/command-line-options.php#sharpen](http://www.imagemagick.org/script/command-line-options.php#sharpen)

---

### Post by RaZe42 on 2010-09-19
Thank you good sir! I was just about to dive into the Imagemagick documentation!

convert creates a copy of the image it's working on, correct? So to modify the source image I should use mogrify.(If I've understood this right.)

---

### Post by lykeion on 2010-09-19
Glad to be of help, and regarding convert vs mogrify you're right:

convert -resize 50% a.jpg b.jpg
will read a.jpg resize it and write to b.jpg (leaving a.jpg untouched)

mogrify -resize 50% a.jpg b.jpg
will modify both files

If satisfied, please tag thread as SOLVED to let others find solutions easily.

---

### Post by RaZe42 on 2010-09-19
Okay, so I got this working!

Here's my noobish little script
```
#! /bin/bash
echo "Files to be processed:"
ls *.jpg
mkdir out/
for file in *.jpg;
  do
    convert "$file" -resize 90% out/"$file"
    convert "$file" -sharpen 0x0.5 out/"$file"
#1
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#2
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#3
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#4
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#5
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#6
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#7
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#8
    convert out/"$file" -resize 85% out/"$file"
    convert out/"$file" -sharpen 0x0.5 out/"$file"
#9-USM
    convert out/"$file" -unsharp 1x0,7+1+0.05 out/"$file"
done
echo "All files processed."
espeak -v en-us "All done. Repeat. All done."
exit
```

Just place the script in the same folder as the images, and run it.
I know that the actions bit #1-8 could be compressed into something smarter, but I'm too lazy right now. I'll probably change the sharpening amount after some experimenting. Also, the espeak on the end is just to notify me when it's done. 
And I'm happy to say that you can see a clear difference between a step-resized image and an image which has been resized in one step and then sharpened.

---

