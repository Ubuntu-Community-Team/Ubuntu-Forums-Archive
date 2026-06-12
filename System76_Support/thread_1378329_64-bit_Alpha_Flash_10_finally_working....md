---
title: "64-bit Alpha Flash 10 finally working..."
date: 2010-01-11
forum: System76 Support
---

### Post by samalex on 2010-01-11
Hi Everyone,

This weekend I tried installing the 64-bit Alpha Flash 10 on my PanP5 system and it finally worked!  It looks like they refreshed it on December 8, 2009, and with me now running Firefox 3.5.7 (Shiretoko build) I figured I'd try it again.

After uninstalling the 32-bit Flash player and the wrapper I downloaded the new Flash plugin from [here]("http://labs.adobe.com/downloads/flashplayer10_64bit.html"), copied it to ~/.mozilla/plugins and Firefox opened with no Segmentation Fault errors which is what I used to get.

I've tested it with about every Flash site I can think of, and thus far everything's running great.  The [Release Notes]("http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html") say there's still some problems that could creep-up, but other then webcam support still not being there it seems to be working great.  I pointed the Hulu Desktop app to the new plug-in, and though it worked, about 30 minutes into a video Hulu hosed with some generic error and closed.  I don't know if it's because of the Flash plugin or what, but Hulu Desktop played MUCH smoother with the 64-bit Alpha Flash plugin than it ever did with 32-bit Flash going through the wrapper.

Anyway, FYI if anyone wants to give this a try.

Take care,

Sam

---

### Post by 3Miro on 2010-01-11
Flash 64 Alpha works well enough, but I still have some problems with it. On my panp4n Hulu fails to open from within the browser, it open as the separate layer, but I have not tested it on a long video.

The bad thing is that it worked fine a few days ago.

---

### Post by samalex on 2010-01-11
> **3Miro said:**
> Flash 64 Alpha works well enough, but I still have some problems with it. On my panp4n Hulu fails to open from within the browser, it open as the separate layer, but I have not tested it on a long video.

The bad thing is that it worked fine a few days ago.

Hmm, not sure.  I just installed it last night and though I haven't had much time to really pound on it, it's been working thus far.  I just hope they release an updated version or possibly a Beta version soon with Webcam support... that's the only thing I'd love to have.

As for Hulu, I don't think I tested it in the browser though because I just use Hulu Desktop... but as I said it worked there very well until Hulu errored and closed, though I can't pin that on Flash just yet.

Take care,

Sam

---

### Post by Derath on 2010-01-11
I've been using an older alpha for a long time, the only problems I've come across is occasional video glitches (i.e. a frame flashing in incorrectly like a title screen flashing in during a game for < 1 sec.). Going to give this version a run though

Panp4n

---

### Post by no2498 on 2010-01-11
glad i seen this post its what im looking for 
flash 10 is good but the web cam wont come on
will flash 9 work on 910 ?

---

### Post by samalex on 2010-01-12
> **no2498 said:**
> glad i seen this post its what im looking for 
flash 10 is good but the web cam wont come on
will flash 9 work on 910 ?

I couldn't find any info on 64-bit Flash 9 to see whether or not it has webcam support, but if it did I could see switching between Flash 9 and 10 depending on what I wanted to do.  It should run with whatever version is in the ~/.mozilla/plugins directory when Firefox opens.

But for now Alpha 64-bit Flash 10 is working well enough for now.  Hopefully the final 64-bit version will be out sometime this year.

Sam

---

### Post by samalex on 2010-01-14
Adobe does say Webcam support in the 64-bit Alpha Flash 10 plugin is not enabled, but I've found a number of sites that work when testing the Flash webcam:
[http://oldes.multimedia.cz/swf/mx-webcam.html](http://oldes.multimedia.cz/swf/mx-webcam.html)
[https://www.makethechange.com.au/secure/chatsoft_9/webcamtest.html](https://www.makethechange.com.au/secure/chatsoft_9/webcamtest.html)
[http://help.yahoo.com/l/us/yahoo/messenger/messenger10/videocall/ms10tavdcltestcam.html](http://help.yahoo.com/l/us/yahoo/messenger/messenger10/videocall/ms10tavdcltestcam.html)

These all work... the picture is really grainy, but it works none the less.  I wonder why these work but Stickam nor UStream will stream video with the webcam.  

For anyone else using the 64-bit Alpha version of Flash I'm curious if these work for you, and if so what about video broadcasting through UStream or Stickam.

Take care,

Sam

---

### Post by samalex on 2010-01-15
I posted an update to this on another thread... I got webcam streaming working with UStream and Stickam with the Alpha 64-bit Flash and Firefox.

Here's the thread-
[http://ubuntuforums.org/showthread.php?p=8669775#post8669775](http://ubuntuforums.org/showthread.php?p=8669775#post8669775)

Thanks --

Sam

---

