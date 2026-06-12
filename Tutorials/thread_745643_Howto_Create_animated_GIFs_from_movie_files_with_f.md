---
title: "Howto: Create animated GIFs from movie files with free software in four easy steps"
date: 2008-04-04
forum: Tutorials
---

### Post by nchase on 2008-04-04
[SIZE=3]***This was originally a blog post; see it in its original form [here]("http://blog.ahfr.org/2008/03/making-animated-gifs-with-free-software.html"). The original post contains information that is not in this forum post because HTML is not allowed here.***[/SIZE]

MPlayer is a pretty powerful tool for processing video files. It has a built-in command line option that will export specified movie frames to a GIF, but the problem with this is that the resultant GIF looks terrible.Such a feature seems like it would make the guide I'm presenting here obsolete, but the problem with the feature is that the resultant GIF looks terrible: too few colors. As far as I've seen, the way to get good quality animated GIFs using only free software involves using a combination of MPlayer's command line tools and a little bit of elbow grease in The GIMP. We will export the desired segment of video to a series of jpeg files, then use The GIMP to combine those files into a nicely animating GIF that should look as good as the original video. I believe that it is possible to get MPlayer and The GIMP together in a script that will allow the end user to simply point the script to the desired movie file and the desired segment and the script will do all the "dirty work" and create the GIF. This is my end goal, but I have not taken the time necessary to learn any of GIMP's scripting language. If there is a pre-existing solution that allows one to do what I am trying to show here, I'd love to know about it, so please let me know.


**Step 1:**
```
sudo apt-get install gimp mplayer
```

**Step 2:**
```
mplayer -ao null -loop 0 -ss 0:11:22 -endpos 5 file.avi
```This command will display the segment of file.avi on your screen that runs from 11:22  to five seconds later (11:27). It will loop infinitely until you close the window or send a ctrl+c to the terminal window. This command is useful for figuring out what your GIF will look like before you make it. The audio output will not be heard (is set to null)

**Step 3:**
```
mplayer -ao null -ss 0:11:22 -endpos 5 file.avi -vo jpeg:outdir=moviedirectory
```This command actually creates the jpeg files you will need to make your animated gif. It is similar to the other command, but nothing is displayed on screen, and the command will not loop forever. The command will output the segment to a series of jpeg files in a directory called "moviedirectory".

**Step 4:**
Now that we have our directory full of jpegs, we should open the first of these files in The GIMP. Then, open the remainder of the images in the directory as layers (File -> Open As Layers). Every image in that directory should now be a layer. Now save the file as a .gif and choose to "save as animation" as opposed to "flatten image." Click export.  Lastly, it is important to make sure "loop forever" is checked if you want a GIF that loops forever. The other options here can drastically change the effect of your gif because they change the speed that the gif is displayed at. A relatively fast gif will have a 15 millisecond delay between frames. The default delay of 100 ms is a bit slow in my opinion. Under frame disposal where unspecified I select "one frame per layer." I check "Use delay entered above for all frames" and "Use disposal entered above for all frames." Here is an example of an end result:

[IMG]http://i31.tinypic.com/2wm3xpe.gif[/IMG]

If you find that your image is too large, it is often helpful to resize it to be a bit smaller. This can help with the image's performance.


As Firefox is often the platform where people will be viewing your animated gif files, it is also a good tool to use to test them to see what the final product looks like.

:guitar:

---

### Post by reclusivemonkey on 2008-04-05
I LOVE Rumblefish, its one of my favourite films ever. That fight scene is one of the most gloriously outrageous ones in cinema history!

---

### Post by nchase on 2008-04-05
Yes sir. 8)

---

### Post by cor2y on 2008-04-11
Thank you for the easy how to.

---

### Post by myster1982 on 2010-08-24
Very good.

But i can recommend try to download VideoCharge Studio. I think that it can help your for processing lot of files.

---

### Post by regnw on 2011-08-17
i use [gifgear.com]("http://gifgear.com") - free online animator

---

### Post by dcsoldschool53 on 2011-09-07
I have not tried this yet, but I will soon. Thank you.

---

### Post by EdTheUniqueGeek on 2011-10-07
Good write up.
Anyone know if there is a way to resize the output to a smaller size in that mplayer command?
I have a video that is 640x336. I would like to make the jpeg files smaller than the original video.
Thanks.

---

### Post by SeijiSensei on 2011-10-07
> **EdTheUniqueGeek said:**
> Anyone know if there is a way to resize the output to a smaller size in that mplayer command? I have a video that is 640x336. I would like to make the jpeg files smaller than the original video.

Shrink the image in the GIMP after you've created it with Image > Scale.

Having made numerous animated avatars using a similar technique to that described by the OP, I have a couple of additional suggestions.  Most of these are designed to minimize the size of the file to conform to sites' requirements.

1)  If the source file is an animation rather than live-action, it's likely that many of the frames are duplicates.  Animation is often done "on twos" or "on threes" which means a 24 frame/sec video often contains only 12 or 8 unique frames each second.  I open all the source frames in an image viewer like Gwenview and use just the frames that differ from their predecessors.  You can also do this in the GIMP dialog box that appears using "Open as Layers."  You can step through the list of images and watch the preview to see which differ.

2)  Most video is shot at either 24 or 30 frames per second.  That means the delay between frames is about 35-40 milliseconds.  If you select individual frames that aren't equally spaced, you may want to play with the timings so that some frames remain on screen longer than others.  In GIMP, you can do this after you save the initial GIF.  First specify an appropriate default delay like 40 ms, then save the file.  Re-open the file in GIMP and open the Layers window with Ctrl-L.  You'll see the timings appear next to each frame.  You can change the timings by simply double-clicking the timing texts and changing the value from, say, 40 ms to 120 ms, if there were two duplicates of each frame in the original.

3)  With 720p and 1080p material becoming more common, you'll often want to cut out a square portion of the image to use as an avatar. In GIMP, first assemble all the frames you want using Open as Layers.  Then bring up the toolbox with Ctrl-B and choose the rectangular selection tool in the upper-left-hand corner of the toolbox.  Now you can specify either the aspect ratio of the selection you prefer (e.g., 1x1) or the size of the selection in pixels.  If you want a square image, fix the selection size to the vertical height of the image, e.g., 720x720 for a video at 720p (1280x720 px).

4)  Sometimes it's nice to put a frame around the image.  This is simple to do in GIMP.  Choose Filters > Decor > Add Frame.  I like nested frames with a black outer border and a white spacer between the frame and the image.  To achieve this, I set the border widths to 1 px, choose white with the color tool, then add the frame.  I repeat the procedure with a black frame. 

Here are a [few examples](http://forums.animesuki.com/album.php?albumid=115) I've made using these techniques.

---

### Post by EdTheUniqueGeek on 2011-10-07
Wow. Thanks for the reply and extensive explanation. I really appreciate it.

> Shrink the image in the GIMP after you've created it with Image > Scale.

Yeah. I tried doing that but having as many as 250 jpeg files in the output directory to resize can be very cumbersome. Unless Gimp has a way of doing it batches that I'm not aware of.

I found my new favorite site over at [http://iwdrm.tumblr.com/](http://iwdrm.tumblr.com/) that has some really cool animated gifs from movies and I wanted to try to do the same with some of my favorite scenes from movies.

---

### Post by SeijiSensei on 2011-10-07
> **EdTheUniqueGeek said:**
> Yeah. I tried doing that but having as many as 250 jpeg files in the output directory to resize can be very cumbersome. Unless Gimp has a way of doing it batches that I'm not aware of.

I meant to resize the image in the GIMP after you've added all the layers.  Once you've added the layers, GIMP treats the image as a single entity for tasks like resizing and cropping.

You can also write a little bash script to resize all the images in a directory.  Something like this:

```

#!/bin/sh
# script to resize images in a directory
IMAGEDIR=/path/to/image/directory
NEWDIR=resized
SCALE='50%'

cd $IMAGEDIR
mkdir -p $NEWDIR

for f in *.jpg
do
    convert $f -resize $SCALE $f $NEWDIR/$f
done


```

This uses the [convert]("http://www.imagemagick.org/script/convert.php") command from the ImageMagick package.  Run "sudo apt-get install imagemagick" to make sure you have it installed.

Replace IMAGEDIR and NEWDIR which your own choices.  The scale factor can be a percent, a numerical value like 200 which changes the width to that size in pixels and adjusts the height proportionately, or any of a number of other options shown [here](http://www.imagemagick.org/script/command-line-processing.php#geometry).  The rescaled images will be placed in IMAGEDIR/NEWDIR, and the originals preserved.

---

### Post by EdTheUniqueGeek on 2011-10-07
Awesome. Perfect.
Thanks again.

---

### Post by EdTheUniqueGeek on 2011-10-07
Ok. So I have created an animated gif. It runs fine locally on my computer if I launch it with Firefox and Chrome. However, if I post it anywhere like Google+ or Tumblr, it doesn't work.
See:
[http://edtheuniquegeek.tumblr.com/post/11142900893/my-first-attempt-at-creating-an-animated-gif-and]("http://edtheuniquegeek.tumblr.com/post/11142900893/my-first-attempt-at-creating-an-animated-gif-and")

And I know for a fact both services will display an animated gif.
Anyone have an idea why it doesn't work?

---

### Post by SeijiSensei on 2011-10-09
> **EdTheUniqueGeek said:**
> Ok. So I have created an animated gif. It runs fine locally on my computer if I launch it with Firefox and Chrome. However, if I post it anywhere like Google+ or Tumblr, it doesn't work.
See:
[http://edtheuniquegeek.tumblr.com/post/11142900893/my-first-attempt-at-creating-an-animated-gif-and]("http://edtheuniquegeek.tumblr.com/post/11142900893/my-first-attempt-at-creating-an-animated-gif-and")

And I know for a fact both services will display an animated gif.
Anyone have an idea why it doesn't work?

The one on Tumblr was converted to a jpeg.

---

### Post by EdTheUniqueGeek on 2011-10-11
> The one on Tumblr was converted to a jpeg.

Hmmmm....well that sucks.

---

### Post by EdTheUniqueGeek on 2011-10-11
Fixed it. 

[http://edtheuniquegeek.tumblr.com/post/11312444370/trying-again]("http://edtheuniquegeek.tumblr.com/post/11312444370/trying-again")

The tip is, if using Tumblr, you need to post as a Text post instead of a Photo post.
More info here:
[http://tumblring.net/tumblr-animated-gif-inserting-and-displaying/]("http://tumblring.net/tumblr-animated-gif-inserting-and-displaying/")

---

### Post by EdTheUniqueGeek on 2011-10-13
So I have made a few animated gifs and posted on my site at edwardcrosby dot com. However, I am noticing that my output doesn't seem to have high quality like the source.
Example: I am currently trying to output a clip from In the Mouth of Madness with the same command as given in the original steps of this thread like so:

```
mplayer -ao null -ss 0:02:55 -endpos 10 MouthOMadness.m4v -vo jpeg:outdir=moviedirector
```

Here is the process of that command:
```

MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing MouthOMadness.m4v.
libavformat file format detected.
[lavf] stream 0: video (h264), -vid 0
[lavf] stream 1: audio (aac), -aid 0, -alang eng
VIDEO:  [H264]  716x368  24bpp  90000.000 fps  428.7 kbps (52.3 kbyte/s)
Clip info:
 major_brand: mp42
 minor_version: 0
 compatible_brands: mp42isomavc1
 encoder: HandBrake 0.9.5 2011010300
jpeg: Progressive JPEG disabled.
jpeg: Baseline JPEG enabled.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
AUDIO: 48000 Hz, 2 ch, s16le, 160.0 kbit/10.42% (ratio: 19997->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
AO: [null] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 2.73:1 - prescaling to correct movie aspect.
[swscaler @ 0x7f4072519620]using unscaled yuv420p -> rgb24 special converter
VO: [jpeg] 716x368 => 1006x368 RGB 24-bit 
jpeg: moviedirector - Output directory successfully created.
A: 185.0 V: 185.0 A-V: -0.000 ct: -0.052   0/  0  8% 29%  0.8% 0 0 

Exiting... (End of file)

```

Between that and the steps used in Gimp as outlined in the steps the animated gif comes out looking no so clear. Here is the image from In the Mouth of Madness.

[http://www.edwardcrosby.com/animated/ItMoM.gif]("http://www.edwardcrosby.com/animated/ItMoM.gif")

[IMG]http://www.edwardcrosby.com/animated/ItMoM.gif[/IMG]


Is there a way to keep the quality of the source video without any degradation as seen in my final animated gif?

---

