---
title: "Stream via flash"
date: 2008-11-23
forum: Ubuntu Studio
---

### Post by mastermindg on 2008-11-23
I'm not sure if this is right place to put this, if not let me know:

I have a large movie collection which I have digitized. I would like to stream these videos via my local web server to serve my local network. I would like to be able to stream on-the-fly, so rather than re-encode the video, basically creating a container thru which I can stream over the network.

Any useful links/comments would be great :)

---

### Post by mastermindg on 2008-11-23
I downloaded Adobe Flash Media Server 3 (Dev). I'll play with this for a while to see how it goes. It's limited to 10 connections, but that's plenty for my local network.

[Get it here]("http://blog.multimediacollege.be/2008/07/installing-flash-media-server-3-on-ubuntu-804/")

---

### Post by mastermindg on 2008-11-23
So, using VOD service, I can do on-the-fly conversions from mp3, flv, and mp4. My question is:

How do I convert from mpeg2 (dvd) to mpeg4 (mp4)?

---

### Post by mastermindg on 2008-11-23
So, I'm using AviDemux to convert, however for some reason the sample vod player is giving me a "connectionerror" when trying to play my converted video. I have verified that all of the video/audio codec's are exactly the same as the sample mp4 files. 

If anyone has any advice regarding FMS that would be great. Thanks.

---

### Post by mastermindg on 2008-11-23
Figured out the error. Wasn't using mp4: before the filename.

---

### Post by thorgal on 2008-11-23
what kind of network is it ? how many network clients will view your videos simultaneously ?

you can use VLC to start a video server on your network. No need to convert anything if bandwidth is not an issue.

I personally have a MythTV system in my network where I can view anything (but mostly my recorded TV shows in mpeg2). If you have 2 simultaneous clients on a wireless network, it may be problematic. On an ethernet network, no problem. The MythTV module for other videos is MythVideo. You configure it by telling where you have your videos, and you view them through mplayer or xine via MythTV. Works nice. It of course requires that you have a MythTV backend somewhere and have MythTV frontends that can connect to it. It's a bit lengthy to configure but is worth it. MythTV does not have to used with TV signals necessarily. It can be used just for video serving as well as music and pictures.

---

### Post by mastermindg on 2008-11-23
I'm connecting via wireless throughout the house. Because of this streaming/buffering is essential; regardless of the connection speed at the router wireless is by nature inconsistent. I would like to host my video collection (NOT recorded movies) so that ANY web-enabled system can watch the videos without the need to install ANY software.

VLC allows streaming of video, yes, but this is not compatible with ALL web-enabled devices. This is why I've chosen Flash, because it is widely used and is pre-installed. 

In summary, this needs to be a solely server-side solution.

---

### Post by mastermindg on 2008-11-24
Well, I've figured it out.

FMS3, installed on Ubuntu Ultimate with Apache2. Simply copy the /opt/adobe/fms/sample/vod/ directory to a virtual directory and run vodtest.html. You can customize the path of the media files or create symbolic links to the default directory. Customizing the page isn't so hard, the actionscript is in a text file.

Thanks all for the help :lolflag:

---

