---
title: "How do I make a video of jpg's, with long transitions?"
date: 2010-01-25
forum: Ubuntu Studio
---

### Post by jobar on 2010-01-25
Hi.

I have several series of photographies (jpg's) of aurora borealis. A normal exposure time on my images is 15 sec.

I want to merge them in to a video where each image is shown for about 15 sec before the next appear. This I know how to do in ffmpeg.

My problem is that I need to have a transition between each image. The ideal would be something like a 10 sec fade.

Anyone know how to do this? I would prefer some command line option since I plan to do this on quite many series of images, but any suggestion is welcome.

Best regards
jobar

---

### Post by houseworkshy on 2010-01-25
I don't know how to do it in command lines but it is fairly easy to do.  This is really a tread bump rather than an answer as I'd quite like to know for myself. Meanwhile you could use gimp gap to generate video from your images and then when they were in video format drop them into kdenlive and use the transitions to stitch them together. A command line way of doing the above task would be very handy.

---

### Post by lisati on 2010-01-25
I haven't done it myself but it might be worth checking out blender (I use other software for most of my video editing stuff)

---

### Post by m0o on 2010-01-25
[FONT=monospace]The best method is using ffmpeg, a simple way to make a directory full of images into videos is:

```
ffmpeg -f image2 -i image%d.jpg video.mpg
```

Read up on the manual (man ffmpeg or [html documentation]("http://ffmpeg.org/ffmpeg-doc.html")) for detailed video options like frame rate, encoding, etc. It's really worth the read because you can control your videos settings precisely. 

Here is a [guide]("http://electron.mit.edu/%7Egsteele/ffmpeg/") that demonstrates this with ffmpeg and mencode. 
[/FONT]

---

### Post by jobar on 2010-01-25
Well. I've used ffmpeg to do a lot of things for me the past feve years and I love it. But it still doesn't solve my problem of having a 10 sec fade between the images in the produced film. I've "scrolled down" the user manual of ffmpeg now and I cant find anything about fading between the images.

---

### Post by Albert25 on 2010-01-25
I haven't tried any of this, but...

It looks like [DVD-Slideshow]("http://dvd-slideshow.sourceforge.net/wiki/Dvd-slideshow_0.8.0") can do that. As far as I can tell, it always produces DVD video, so you would be limited to that low resolution.

Maybe [http://users.telenet.be/acp/ppmfilter/](http://users.telenet.be/acp/ppmfilter/) can do it.

You can definitely do that with some smart scripting and ImageMagick. I know it can blend 2 pictures together. So you could loop over your original image-XX.jpg files to create image-for-video-XX.jpg files, where the images without effects would probably just be links to the originals, and the others would be new images produced by imagemagick. Then you would use your normal ffmpeg command to convert the new jpg sequence to video. Fun scripting for a rainy day...

---

### Post by jobar on 2010-01-25
tnx!

I'll try...

---

### Post by LuridCinema on 2010-01-25
You will need a Video editor like OpenShot or KdenLive to do the fades. Each one has transitions so you can change it up.

---

### Post by chewearn on 2010-01-25
> **Albert25 said:**
> You can definitely do that with some smart scripting and ImageMagick. I know it can blend 2 pictures together. So you could loop over your original image-XX.jpg files to create image-for-video-XX.jpg files, where the images without effects would probably just be links to the originals, and the others would be new images produced by imagemagick. Then you would use your normal ffmpeg command to convert the new jpg sequence to video. Fun scripting for a rainy day...

Here is how to make fading pictures using imagemagick.

Let say your picture is "000.jpg" with dimension 800x600.

First create a black picture "100.jpg" of the same dimension:
```
convert -size 800x600 xc:'rgba(0,0,0,1)' 100.jpg
```Then, dissolve 000.jpg onto 100.jpg, from 10% to 90%
```

for i in `seq 10 10 90`; do  composite -dissolve $i 100.jpg 000.jpg "0$i.jpg" ; done
```Now, you got a sequence of pictures which fade to black from 000.jpg, 010.jpg,... 100.jpg.

---

### Post by FakeOutdoorsman on 2010-01-25
> **chewearn said:**
> Here is how to make fading pictures using imagemagick.

Let say your picture is "000.jpg" with dimension 800x600.

First create a black picture "100.jpg" of the same dimension:
```
convert -size 800x600 xc:'rgba(0,0,0,1)' 100.jpg
```Then, dissolve 000.jpg onto 100.jpg, from 10% to 90%
```

for i in `seq 10 10 90`; do  composite -dissolve $i 100.jpg 000.jpg "0$i.jpg" ; done
```Now, you got a sequence of pictures which fade to black from 000.jpg, 010.jpg,... 100.jpg.

Nice tip, chewearn.

---

### Post by JC Cheloven on 2010-01-25
> **LuridCinema said:**
> You will need a Video editor like OpenShot or KdenLive to do the fades. Each one has transitions so you can change it up.
+1 for OpenShot
I used it for a very similar purpose than the OP, and loved it. Also it is a general video editor, in case you'll need anything more.

---

### Post by jobar on 2010-07-31
Hi again folks.

Thanks for all the tips. I've used them on several smaler tasks, but they still doesn't solve my original problem.

I'll describe my full intention with my images, but not all of it are a problem. I'll just include it to give you the full picture. Maybe someone have a completely different solution on the whole problem.

Problem:
I have several series of images of aurora borealis, and each series contains about 1600 hi-resolution images. This is from an exposure every 6 seconds thruout one whole night.

I need to generate a fadeing transition between every image. 
There is not that much difference between six seconds on the nigt sky - even with aurora, and thru small scale testing, I've found that a transition of 10 images is sufficient to get a nice "continious" feeleng on the video. But to generate this manually 1600 times just isn't an option. (and these numbers are just for one of my many image series :)

I need a more smooth way of generating these nearly 15000 images. One suggestion is some clever imagemagick scripting. I love imagemagick, but I'm not particulary good with scripting. If anyone have some suggestions on this, I would be grateful!!* (see footnote)

The rest: 
Later I will stitch these approx. 16000 images together to a hi-res. time laps vidio. Thats the easy part.
The 16000 images correspond to one image every 0.6 second. If I use a framerate of 25, this would give smooth timelaps video of approx 10.5 min of the whole aurora night.

I could of cource buy photoshop and do this on a windows computer at work. A friend of mine says it's possible with som clever photoshop automation scripting. But my collegues continiously nags me (friendly of cource) for choosing linux on my private and work computers, so I refuse to do so out of mere principle :)

Hope anyone can help. In advance thanks.

Jobar


*
(The output generated between two images i.e. "original_img01.jpg" and "original_img02.jpg", should preferably be a series of "img01.jpg" to "img11.jpg", where "img01.jpg" is the same as the "original_img01.jpg", and "original_img02.jpg" is the same as "img11.jpg".
"img02.jpg" to "img10.jpg" should be the generated fadeing transition images.
File names are not important as long as they have some sort of continuous numbering.)

---

### Post by jobar on 2010-08-03
Problem solved:

1
Make 10 image fading transition between every following image in the working directory and saves the result, with increasing file numbering, to directory "dir":
```
convert *.jpg -delay 20 -morph 10 dir\image%05d.jpg
```

2
Makes an .avi film of every jpg in the directory. Frame rate 30 fps, bit rate 3600, codec mp4:
```
mencoder "mf://*.jpg" -mf fps=30 -o test_b3600.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=3600
```

3
Film made - me happy :)

---

### Post by Avinash Zala on 2011-05-18
Hi,

Thanx Jobar because video transition works successfully.

and yah....."mencoder "mf://*.jpg" -mf fps=30 -o test_b3600.avi -ovc lavc -lavcopts vcodec=msmpeg4v2:vbitrate=3600" this one is not working because i have used ImageMagick but i have generated video through Convert

but i have problem of transitions that is i need different delay between all images

What i need is Image display upto 10 sec then after morphing image display quickly and then after next image display upto 10 sec


please reply me quickly...:(

---

