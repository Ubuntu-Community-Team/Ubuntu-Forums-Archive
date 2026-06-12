---
title: "Producing videos with a linux netbook, digital camera, and limited bandwidth"
date: 2009-07-15
forum: Ubuntu Studio
---

### Post by accord on 2009-07-15
*[Click here]("http://accordt.blogspot.com/2009/06/producing-videos-with-linux-netbook.html") to see this page at [my blog]("http://accordt.blogspot.com/").*

The processing power on a netbook is often insufficient for rendering video files. Either it takes a unacceptable amount of time, or fails comletely. After experimenting a bit, here is a quick way to produce videos while traveling with your camera and netbook.

First, use your camera to record video clips. You should have a rough idea of the storyboard of your final video. Split them into scenes, and record them separately.

My camera, Fujifilm F100fd, records video into AVI files. For example, I decide to make an intro, then a panoramic scenic view, and the ending. We will have 3 files: **DSCF0001.AVI**, **DSCF0002.AVI**, and **DSCF0003.AVI**. Transfer them onto the computer either using a card reader or USB cable.

Next, we join the video files by simply attaching them together with 'cat'.

```
cat DSCF0001.AVI DSCF0002.AVI DSCF0003.AVI > output.avi
```


You can also rearrange scenes if you like.

```
cat DSCF0003.AVI DSCF0002.AVI DSCF0001.AVI > output.avi
```

Sometimes, particularly with videos from cameras, the sound might be dropped in a couple of frames. The header of the AVI file also has to be reconstructed. We re-sync the sound and video with mencoder (part of the mplayer package):

```
mencoder -forceidx -oac copy -ovc copy output.avi -o output_synced.avi

```

Now you have a synced AVI that is cut, rearranged, and suitable for viewing. If you wish to upload to youtube, you can compress the film to a smaller format. I tried to export to DivX without luck, while WMV worked for me. Here is the command to convert to WMV:

```
ffmpeg -i output_synced.avi -vcodec wmv2 -acodec wmav2 output_final.wmv

```

Alternatively, you can try WinFF and experiment with various video formats, and see which one fits you best. The video is all done and ready for upload! FireUploader may be able to assist you in uploading the file.

With this method I was able to post quite a few videos without the trouble of using a real video editing software, or rendering of video files. I hope people with limited computer resources, travelers, for example, will find this helpful and produce more interesting videos!

---

### Post by NLEatwork on 2009-07-15
Eugenia outlines a similar technique which allows you to trim the videos in a second-accurate way (perhaps it can also be frame accurate?).

```
fmpeg -ss 00:00:01 -t 00:00:15 -i "video1.m2t" -acodec copy -vcodec copy "edited-video1.m2t"
```

[http://eugenia.gnomefiles.org/2009/05/20/basic-video-editing-with-ffmpeg-on-linux/](http://eugenia.gnomefiles.org/2009/05/20/basic-video-editing-with-ffmpeg-on-linux/)

Hope this helps anyone else on netbook strength cpus.

---

