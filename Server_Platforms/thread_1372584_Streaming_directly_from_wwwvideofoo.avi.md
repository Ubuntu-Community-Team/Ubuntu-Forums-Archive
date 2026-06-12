---
title: "Streaming directly from /www/video/foo.avi"
date: 2010-01-04
forum: Server Platforms
---

### Post by Talix on 2010-01-04
Hey (:

I don't know why, but I can't seem to just play video files (stream them) directly through the internet using MPC or any other media player. It is a bit weird, because I think I was able to just a month ago. I have made some changes to the general setup of the apache server, but nothing major, and I have no chance of reversing it all.

Instead, when I try opening the url using "Open file" it doesn't just open it an begin playing from the internet, but instead appears to be frozen. However, If I let it be "frozen" long enough, it will eventually play the file, indicating that it has downloaded the entire file to a temp location on the hard drive.

Is it something with the permissions?
Actually, I went and made everything in /var/www/ 777, as it is not known by a domain name or registered anywhere. I am just connecting though my IP address as the server is located locally. Even this didn't help.

Can you help me?

---

### Post by Drezard on 2010-01-04
The first thing I would do is try it from another computer. If its still not working from another computer, try another media player. (Maybe a media player update). If both of those options dont work, then maybe start looking into capturing a few of the packets off the wire.

---

### Post by Talix on 2010-01-04
> **Drezard said:**
> The first thing I would do is try it from another computer. If its still not working from another computer, try another media player. (Maybe a media player update). If both of those options dont work, then maybe start looking into capturing a few of the packets off the wire.I did try it from another computer (in the other side of the country ;) ), I even tried from the computer HOSTING the files -.-

How can I capture packets "off the wire" and what does it mean?

---

### Post by Talix on 2010-01-05
anyone? :s

---

### Post by Talix on 2010-01-06
-.-

---

### Post by Cyked on 2010-01-06
Not to hijack the thread, but I'm curious about this as well.  I have a, lets say, vanilla install of apache.  In FF from another machine accessing an MP4 vid I get the freezing symptom as the whole vid loads.  If I access it on my 2g orginal iphone it plays right away, but if I pause it doesn't continue loading, like its streaming, so it pauses and stutters a lot.  On a computer with FF if I refresh any time after the vid loads the whole process starts over.

I'm just getting into this piece as I just got a dig. camcorder for xmas.

---

### Post by firefly2442 on 2010-01-07
Does it matter what type of video format it is (.avi, mpeg, OGG, etc..)?

For capturing packets you could use something like Wireshark but to be honest I'm not sure how that will help you here.

For Apache, when you say "open the file", it's actually downloading the whole thing to a temporary directory.  Like you said, I'm guessing it's just taking a little bit to download the video before it can actually play it.  If you want to truly stream the video and have it play while buffering/downloading I think you'll need to look into some alternatives.  Apache at the base level is fairly simple in just serving up files for download.

I did some quick google searching and came across Flowplayer:

[http://flowplayer.org/](http://flowplayer.org/)

I guess it lets you stream FLV videos (so you'd have to convert the videos).  But then at least they would be streaming.

VLC can also stream video:

[http://www.videolan.org/vlc/streaming.html](http://www.videolan.org/vlc/streaming.html)

But this probably isn't appropriate if you have a website with lots of visitors.

Anyway, hope this helps a little or at least gives you some ideas to start with.  Cheers.  :)

---

### Post by Cyked on 2010-01-07
I found this.
[http://ubuntuforums.org/showthread.php?t=34359](http://ubuntuforums.org/showthread.php?t=34359)

I would think a big consideration for this would be how big are the files you want to stream.  Given a normal res. connection with ATT/comcast/or what have you, even streaming would be extremely slow for things to buffer/queue up (i.e. like pausing youtube and coming back to the page after a chunk has loaded).

FWIW, if I use VLC and open as open network stream, if I pause I have no network activity at all.  If I hit play it just freezes and tries to download, but it can't download fast enough to play the file.

---

### Post by Talix on 2010-01-07
> **Cyked said:**
> I found this.
[http://ubuntuforums.org/showthread.php?t=34359](http://ubuntuforums.org/showthread.php?t=34359)

I would think a big consideration for this would be how big are the files you want to stream.Yeah, the issue is the size of the files. The average size is around 200 mb PER FILE, and thats 20 mins of video.

The ideal way of playing these would be directly from the server, so it wouldn't have to wait those 4-5 mins every time i need to dl 200 mb...

Regarding the link you found, I saw that too, but it was only focusing on sound files, and it even needed codecs. What I want is a solution that just transfers the data, not the already put-together decoded video (which would be waaaay to tough on my little eeepc server as the files I am trying to stream are mostly H264 encodings in HD) and lets the streaming machine put the signal together.

---

### Post by Talix on 2010-01-07
BREAKTHROUGH!!!! (well, partially at least)

I found [this]("http://h264.code-shop.com/trac/wiki/Mod-H264-Streaming-Apache-Version2") module for apache which solves the problem with the files needing to be downloaded completely, instead buffering them while playing.

However, there are two issues, one of them fatal.

[LIST]
[*]Buffering the file means that it is still getting downloaded to a temp dir, not played directly form the server (well, I know that *some* buffering is needed, as it is impossible to play data not "on" the system. The fact that the file needs to buffer, also means that you can't choose to play the file from halfway through the file or start with the ending (if you have watched the first half of the movie). Still, it is better than to wait for the WHOLE file to complete.
[*]This only works with MP4 (as far as I can see). I tried adding the .mkv extension in the httpd.conf file, but it doesn't work - ill try to ask code-shop if it is possible in some way to use other containers than .mp4. (This is the fatal one, I only have .mkv files, just tested the stream with the ONLY mp4 file i had on the server).
[/LIST]
If anyone knows anything, or can come up with ideas on how to enable the .mkv container to also be "streamable" I would be forever grateful.

---

### Post by Cyked on 2010-01-07
> **Talix said:**
> BREAKTHROUGH!!!! (well, partially at least)

I found [this]("http://h264.code-shop.com/trac/wiki/Mod-H264-Streaming-Apache-Version2") module for apache which solves the problem with the files needing to be downloaded completely, instead buffering them while playing.

However, there are two issues, one of them fatal.

[LIST]
[*]Buffering the file means that it is still getting downloaded to a temp dir, not played directly form the server (well, I know that *some* buffering is needed, as it is impossible to play data not "on" the system. The fact that the file needs to buffer, also means that you can't choose to play the file from halfway through the file or start with the ending (if you have watched the first half of the movie). Still, it is better than to wait for the WHOLE file to complete.
[*]This only works with MP4 (as far as I can see). I tried adding the .mkv extension in the httpd.conf file, but it doesn't work - ill try to ask code-shop if it is possible in some way to use other containers than .mp4. (This is the fatal one, I only have .mkv files, just tested the stream with the ONLY mp4 file i had on the server).
[/LIST]
If anyone knows anything, or can come up with ideas on how to enable the .mkv container to also be "streamable" I would be forever grateful.

So you mean instead of getting a mostly blank screen and an hour glass while it downloads you would see the first "image" of the vid while its queuing up/buffering?

---

### Post by firefly2442 on 2010-01-07
Well, if you're trying to serve or stream high quality video off your eee PC I would guess it would be pretty slow.  They're not really meant to be super fast.

---

### Post by Cyked on 2010-01-07
I'm more or less playing around with this since I'm just now trying and researching it.  My goal right now is get an mp4 file play on a computer externally in a way that if you pause the vid it continues to load and then go from there.  At this point I'm not worried about if the file is 100mb and takes 30 min to load.  I'm looking more for what happens, not how fast it is.

---

