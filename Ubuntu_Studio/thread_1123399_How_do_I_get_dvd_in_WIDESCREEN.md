---
title: "How do I get dvd in WIDESCREEN?"
date: 2009-04-12
forum: Ubuntu Studio
---

### Post by pwc on 2009-04-12
Here's a problem using Ubuntu 8.10 that I can't resolve:

1. I shoot video clips of an event using the Canon FS11 in WIDESCREEN.

2.  Dump the clips to my Desktop as MOD files(there are 2 other files with each MOD file that I don't bother with).

3. Change the .MOD extention to .mpg - Now I can use the videos with all video applications(vlc, mplayer, kino, DeVeDe, etc.)

4. Use Kino to edit the video clips and make movie. I set all settings I can to WIDESCREEN and export to a DVD file format. This gives me a final "mpeg" video.

5. Use DeVeDe with the "mpeg" video and create an .iso file - set all to WIDESCREEN.

6.  Use Brasero to burn the .iso image to a DVD.

When I play the DVD to watch on TV it plays in aspect ratio 4:3 and not in WIDESCREEN!

Can someone tell me where I go wrong?

---

### Post by pwc on 2009-04-14
OK I've researched some and found this post by Jonathan Metillon:  [http://ubuntuforums.org/showthread.p...02#post1855229](http://ubuntuforums.org/showthread.p...02#post1855229)
His post does a nice job explaining how to deal with .MOD files.

It sets up a Ruby script to transcode the .MOD file format to DV. It looks like this setup might solve my problem, however now I can't get the script to run. When I do this command:     

                                   transcode -r

I get this:

                                    wayne@antec:~/Desktop/TestVideos$ transcode -r
                                    transcode: option requires an argument -- 'r'
                                    transcode v1.0.7 (C) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg, 2004-2008 Transcode Team
                                    'transcode -h | more' shows a list of available command line options.
                                     wayne@antec:~/Desktop/TestVideos$ 

Can anyone interpret that, I don't know what   "option require an argument --'r' "   means.

Help  -  pwc

---

### Post by thorgal on 2009-04-15
I have no idea what you want to do, but the option requires that you give it something to work on:

transcode -r something
the -r option takes the 'something' after it as an argument, could be a filename or whatever.

I suggest you type
```

man transcode

```
and look for what option -r means.

---

### Post by pwc on 2009-04-15
Thanks Thorgal for your post, it helped get me going again. Now I understand what I was overlooking. Now I can continue working on the big problem of getting WIDESCREEN format on DVD.

pwc

---

