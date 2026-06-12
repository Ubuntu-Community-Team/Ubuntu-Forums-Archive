---
title: "batch image resize GUI"
date: 2009-11-18
forum: Ubuntu Studio
---

### Post by matches on 2009-11-18
Can someone recomend a good batch image resize software?

It is important that I be able to rename resized images.
I like to be able to resize images to thumbnails with a "TH" at the end of the file name.

I would also like it to be a GUI program as well but not as important as changing the name of the file.

Thanks for any help

---

### Post by kayosiii on 2009-11-18
Digikam should be able to do this for you

---

### Post by indytim on 2009-11-19
You can also do it from within GIMP.

IndyTim

---

### Post by lwhistler on 2009-11-20
Not GUI but in my opinion better. You could use ImageMagick and a bash script, or run it from the terminal.  Below is a script I use to: Crop, resize and color correct. It will also add the TH_ prefix.

resize.sh
[php]#!/bin/bash

for image_file in *.JPG
do
convert $image_file -crop 3931x2211+244+528 -resize 1920x1080 -level 0%,81%,1.0 -unsharp 0x2 -quality 100 TH_$image_file
done[/php]Just save it as a .sh file and make it executable. Put it in the same folder as your images and click on it. I use GIMP on one file to get the above settings. To make a file executable: Right click > Properties > Permissions > Check the Execute

Checkout   ImageMagick for all the options you have. [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by ian2112 on 2009-11-20
One other suggestion that I use and find quite easy is to install a nautilus script.  This will put the functionality as a right-mouse button click.

So, I highlight all the images I want to resize and the one right-mouse button click... and it's done.

If you google nautilus script image resize you should lots of options and better descriptions than I can provide here.  The script I installed has a ton of other functionality, too.

Cheers

---

