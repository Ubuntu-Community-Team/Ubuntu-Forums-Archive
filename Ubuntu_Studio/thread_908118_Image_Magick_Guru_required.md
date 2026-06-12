---
title: "Image Magick Guru required"
date: 2008-09-02
forum: Ubuntu Studio
---

### Post by leg on 2008-09-02
This post is related to [another]("http://ubuntuforums.org/showthread.php?t=907283") of mine. If this considered bad form please merge.

I have realised that images I am using on a site of mine are not as small as they could be. The example I gave in the other thread altered a 80x60 png image from 24.6kb all the way down to 1.8kb. I now want to use Image magick to do this to all 3149 images for the site. Basically the steps performed in the Gimp was to uncheck all boxes when saving and change the image mode to indexed. When changing to indexed also select use web-optimised pallette" and remove unused colour from colourmap.

Through Image Magick I have managed to reduce the example to 9.7kb but I am stuck getting any further. Also the command
```
mogrify -channel Indexed * 
```reduced the file sizes by half but in the Gimp shows that the image mode is still set to rgb. Can anyone explain the command sequence required to achieve all the steps I did manually in the Gimp.

Those steps would be switch of 
save resolution
save creation time
save gamma
save background colour
interlacing

and change the mode to indexed removing unused colours. Also make sure that there is no comment appended to the image.

Thanks

---

### Post by leg on 2008-09-02
I have managed to do this with a combination of the following commands.

```
mogrify -channel Index *
mogrify -strip *
mogrify -colours 32
```
These commands got a folder of 3149 png images with a size of 63mb down to 5.6mb.

My test image is currently at 2.43kb and I managed to get it down to 1.8kb with the gimp. So I think I still have an option somewhere that I can use to reclaim every last bit of space. :)

---

### Post by Unterseeboot_234 on 2008-09-03
Thanks for your post. imagemagick is rather undocumented, but I am totally impressed with the multiple ways to do the same things. Have you tried one command line?

```
mogrify -channel Index * -strip * -colours 32
```

The imagemagick command-line is limited to 768 files at one batch. The command-line "convert" will also do many of the same conversions that "morgrify" does. It is my preference to write a short python program to take total control of filenames, filtering, folder destinations, cleanup and so forth. Ruby, perl, shell-script and java will also work beautifully with imagemagick.

---

### Post by leg on 2008-09-03
> **Unterseeboot_234 said:**
> Thanks for your post. imagemagick is rather undocumented, but I am totally impressed with the multiple ways to do the same things. Have you tried one command line?

```
mogrify -channel Index * -strip * -colours 32
```

The imagemagick command-line is limited to 768 files at one batch. The command-line "convert" will also do many of the same conversions that "morgrify" does. It is my preference to write a short python program to take total control of filenames, filtering, folder destinations, cleanup and so forth. Ruby, perl, shell-script and java will also work beautifully with imagemagick.Yes I did try that but I think I got it a little wrong in that I did not have the stars after each command. Also the -channel 32 section seemed to remove to much from the images so I had to leave that out anyway. I think scripts to do these things are a goo idea and will look into that in the future. I used mogrify as I required the same file name but I just copied the folder and practiced on the copy so I always had the originals.

When you say it is limited to 768 files in one batch what does that mean. Does it do 768 of them and then do the next 768 or have any files after that number not been affected?

---

### Post by Unterseeboot_234 on 2008-09-03
The command-line tools in ImageMagick consist of 11 commands that work in the Terminal shell.

**[COLOR="RoyalBlue"][ImageMagick command-lines]("http://www.imagemagick.org/script/command-line-tools.php")[/COLOR]**

"mogrify" overwrites a file after following the options desired. "convert" writes a new file to a new destination. And yes, you are limited to 768 files per command-line execution when using ImageMagick "right out of the box".

When using python I can detail several command-line instructions on one image. python then is the workhorse handling all of the file creation. Because of your post I went looking for my last program written in python for doing this type of image manipulation. It's on my CD backups somewhere. Basically, python runs as a system command much like a robot, completes each cycle before repeating the commands for the next image.

There is one book on ImageMagick which shows the possibilities -- the book is by no means comprehensive. It is in English but with a German accent. $8 as an eDoc on Amazon -- "ImageMagick Tricks". Or, google around for it on the web.

I find I have to google the blogs, the official ImageMagick website and email discussion boards to discover what the optional keywords are and how they are configured. When you installed ImageMagick, you got the docs in html form also which is pretty much the same as the official web site for ImageMagick.
```
usr/share/doc/imagemagick
```

---

### Post by leg on 2008-09-03
Great info thanks. I suppose you could do the same thing with bash scripting or any other language also. Just to clarify (sorry for being dumb) when I ran the above commands it worked through 768 of the files in my folder and then stopped so I have only optimised a sixth of them. Is that correct?

By the way I had found the docs on my hard drive I just don't understand graphics well enough yet to fully understand all of it. I need to do more research I think.

---

### Post by Unterseeboot_234 on 2008-09-04
Just for laughs, I'm attaching my python code. python works as a shell commander because it waits for each loop iteneration to finish before making another evaluation of each item in a list (the conditional). So, you get the strength of python -- file management and system (os.dir['.'] and os.sys).

Good luck. Should you have other thoughts, please communicate. I adore python, java and ImageMagick.

---

### Post by leg on 2008-09-04
Thanks again. By the way have you ever found [this forum]("http://www.imagemagick.org/discourse-server/index.php?sid=b2230c1868ff2f2b1fd2e464c94c782f"). For completeness I will post the bash script I used when I get home.

[edit]I have also found [this page]("http://www.lemur.com/dmm/culch/scriptsfu/index.html") but I have not gone through it properly yet.

---

### Post by borobudur on 2008-10-28
Hi ImageMagick Gurus,
perhaps you could help me too. I'm trying to convert several SVG files to PNG. I was thinking I could do it like this:
```
find . -name '*.svg' -exec convert -resize 80X80 -type png {} \;
```But the convert application tells me:
```
convert: unrecognized image type png.
```Any suggestions?

---

### Post by unutbu on 2008-10-28
Edit: Here is a one-liner that converts svg's to png:
```

mogrify -resize 80x80 -format png *.svg
```
Note that this command does not walk through subdirectories.

----------------------------------------------

No doubt there is a way to do this with bash, but I find it easier to write python scripts:

[php]
#!/usr/bin/env python
import os
for root, dirs, files in os.walk(os.curdir,False):
    for name in files:
        if os.path.isfile(name) and not os.path.islink(name):
            filename=os.path.join(root, name)
            (shortname, extension) = os.path.splitext(filename) 
            if extension=='.svg':
                newname=shortname+'.png'
                cmd='convert -resize 80x80 "%s" "%s"'%(filename,newname)
                os.system(cmd)
[/php]

Save this to a file called svg2png.py
To make it executable:```

chmod +x svg2png.py

```
To run it:

```
cd /path/to/svgs    # change directory to the svgs
~/svg2png.py           

```

The script will recursively walk through all directories below the current working directory, find all .svg files, and convert them to 80x80 .png files. It will also operate properly on files whose names contain spaces.

---

### Post by borobudur on 2008-10-28
Hey! Very nice!! 

The walk through the file structure works fine but there is something wrong with the quality of the converting. The png looks very bad. Any idea what's wrong with the convert command?

---

### Post by unutbu on 2008-10-28
You are right. convert does a poor job converting svg's to png.
This seems to work better:

First, install the librsvg2-bin package from the official repo.
It is a small package: 196KB

Then use this script:
[PHP]
#!/usr/bin/env python
import os
for root, dirs, files in os.walk(os.curdir,False):
    for name in files:
        if os.path.isfile(name) and not os.path.islink(name):
            filename=os.path.join(root, name)
            (shortname, extension) = os.path.splitext(filename) 
            if extension=='.svg':
                newname=shortname+'.png'
                cmd='rsvg -w 80 -h 80 "%s" "%s"'%(filename,newname)
                os.system(cmd)
[/PHP]
It is basically the same script, only 2 differences from my previous script:
1) the cmd has been changed to use rsvg
2) a test was added so the script only tries to convert svg files

---

### Post by borobudur on 2008-10-29
Thanks! Perfect!!

---

