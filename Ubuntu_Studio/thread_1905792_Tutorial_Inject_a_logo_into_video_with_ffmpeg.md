---
title: "Tutorial: Inject a logo into video with ffmpeg"
date: 2012-01-07
forum: Ubuntu Studio
---

### Post by cfhowlett on 2012-01-07
Greetings:

A while back, I inquired about a "Made with Ubuntu (Studio) logo for video/website/misc use.  This was inspired by the ubiquitous  [IMG]https://ssl.apple.com/about/webbadges/images/madeonamac20050720.gif[/IMG] and the apple logo.  For some time, I've wanted to incorporate a little Ubuntu Studio love into my modest multimedia productions.  Finally, I've figured out ONE method.  YMMV.

First, find or create the logo.  I went to [http://design.canonical.com/the-toolkit/]("http://design.canonical.com/the-toolkit/") and downloaded the Ubuntu Studio materials.  I selected the logo I wanted, resized it and reduced the brightness in Gimp.  [http://dl.dropbox.com/u/7001421/Ubuntu%20Studio%20logo.png]("http://dl.dropbox.com/u/7001421/Ubuntu%20Studio%20logo.png")



Then I went to the command line...

**See [http://ffmpeg.org/libavfilter.html#overlay](http://ffmpeg.org/libavfilter.html#overlay)**

24.25 overlay 

Overlay one video [i.e. LOGO] on top of another.

It takes two inputs and one output, the first input is the "main" video on which the second input is overlayed.

It accepts the parameters: x:y[:options] **DAMN EMOTICON!  Should read "x:y[:LETTER"o"ptions**

x is the x coordinate of the overlayed video on the main video, y is the y coordinate. x and y are expressions containing the following parameters:

&#8216;main_w, main_h&#8217;

    main input width and height
&#8216;W, H&#8217;

    same as main_w and main_h
&#8216;overlay_w, overlay_h&#8217;

    overlay input width and height
&#8216;w, h&#8217;

    same as overlay_w and overlay_h 

options is an optional list of key=value pairs, separated by ":".

The description of the accepted options follows.

&#8216;rgb&#8217;

    If set to 1, force the filter to accept inputs in the RGB color space. Default value is 0. 

Be aware that frames are taken from each input video in timestamp order, hence, if their initial timestamps differ, it is a a good idea to pass the two inputs through a setpts=PTS-STARTPTS filter to have them begin in the same zero timestamp, as it does the example for the movie filter.

Follow some examples: 
 	

# draw the overlay at 10 pixels from the bottom right
# corner of the main video.
overlay=main_w-overlay_w-10:main_h-overlay_h-10

[FOR EXAMPLE]
ffmpeg -i forerunnercrawl.mp4 -vf "movie=video-logo.png[logo];[in][logo]overlay=main_w-overlay_w-10:main_h-overlay_h-10[out]" -vcodec libx264 logocrawl.mp4

# insert a transparent PNG logo in the bottom left corner of the input
movie=logo.png [logo];
[in][logo] overlay=10:main_h-overlay_h-10 [out]

[FOR EXAMPLE] 
ffmpeg -i forerunnercrawl.mp4 -vf "movie=video-logo.png[logo];[in][logo]overlay=10:main_h-overlay_h-10[out]" -vcodec libx264 logocrawl.mp4

# insert 2 different transparent PNG logos (second logo on bottom
# right corner):
movie=logo1.png [logo1];
movie=logo2.png [logo2];
[in][logo1]       overlay=10:H-h-10 [in+logo1];
[in+logo1][logo2] overlay=W-w-10:H-h-10 [out]

[FOR EXAMPLE]
ffmpeg -i clean_crawl.mp4 -vf "movie=studio-logo.png[logo1];movie=video-logo.png[logo2];[in][logo1] overlay=10:H-h-10 [in+logo1];[in+logo1][logo2] overlay=W-w-10:H-h-10 [out]" logo_crawl.mp4

I placed the Ubuntu Studio logo on the bottom left and my brandmark on the bottom right.  Check it out: [Click the link, see the flick.]("http://dl.dropbox.com/u/7001421/Kokujin%20Chronicles%20Episode%20007.mp4")

---

### Post by overdrank on 2012-01-07
Please do not create multiple threads. Thread closed.

---

