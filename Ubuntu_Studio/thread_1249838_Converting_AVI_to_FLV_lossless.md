---
title: "Converting AVI to FLV lossless?"
date: 2009-08-25
forum: Ubuntu Studio
---

### Post by Aptana on 2009-08-25
Hey guys. I have been using imTOO FLV Converter via WINE for this for ages, and now I'm wondering if it would be faster and easier to do this without WINE.

Does anyone know a way to convert AVI files to FLV format (suitable for streaming over the web) with very little/no quality loss? End filesize doesn't really matter.

I have tried ffmpeg before and it didn't really give me the results I wanted. Either that or I'm doing it wrong :P

I've Google'd for an hour, but most of the results are just spam with free software downloads. Annoys me to bits :P

Thanks guys.

---

### Post by FakeOutdoorsman on 2009-08-25
FFmpeg can definitely do this, but since you are going from a lossy to lossy format you can not get a lossless quality.  However, perceptively it can look close. I can give you some examples, but I have a few questions to help narrow things down:
[indent]1. What Ubuntu version are you using?
2. How are you presenting this video? (Example: Apache, with JW Player, etc)
3. Do you really need streaming?  Streaming allows seeking before the whole clip is downloaded, but there are additional steps and I have little experience with this.[/indent]

---

### Post by Aptana on 2009-08-26
Thank you for the reply.

1) I'm using Ubuntu Hardy.
2) It'll be on the Apache web server and most likely JW Player, yeah.
3) The video's will be for a youtube-like website so yeah I do really :P

Thanks for you help so far :)

---

### Post by peepingtom on 2009-08-26
I suggest you open a terminal, run ```
man ffmpeg > ~/ffmpeg.manual.txt
``` and read the resulting manual in your home directory. You're trying to do something complicated, the manual is easy to understand though. Also learn what audio/video formats are acceptable to be muxed into flv containers, if you want lossless you can have ffmpeg copy streams into different containers if they don't need to be converted.

---

### Post by FakeOutdoorsman on 2009-08-26
> **Aptana said:**
> Thank you for the reply.

1) I'm using Ubuntu Hardy.
I recommend compiling FFmpeg and x264 yourself to take advantage of the libx264 presets which make encoding much easier:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]
> 2) It'll be on the Apache web server and most likely JW Player, yeah.
You can encode H264/AAC audio and throw it into a FLV container.  This isn't "standard" practice, but it is easier to use the FLV container for streaming than the MP4 container.  With MP4 you would need to use an additional Apache module such as the [H264 Streaming Module](http://h264.code-shop.com/trac).

1. Encode:
```
ffmpeg -i input.avi -acodec libfaac -ab 96k -ac 2 -vcodec libx264 -vpre hq -crf 22 -threads 0 output.flv
```

2. Run it through flvtool2 or [flvtool++](http://mirror.facebook.net/facebook/flvtool++/) to hint the FLV metadata.  I'll use flvtool2 as an example, but flvtool++ is probably a better tool because it doesn't load the whole file into memory to prepare the metadata, and it also doesn't require ruby which can isn't a small package.  You need to use one of these tools or your player, such as JW Player, will have issues playing the video.
```
flvtool2 -U output.flv
```

Now play it with JW Player.  You should be able to seek around in the movie before the whole clip is downloaded.  I think this is all you need to do, but I haven't tested this.

---

