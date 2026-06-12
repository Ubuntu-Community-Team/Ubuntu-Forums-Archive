---
title: "HowtO BLOCK YOUTUBESTREAMING - ANY AUDIO/STREAMING WEBSITES WITH SQUID3.3.8"
date: 2016-01-06
forum: Security
---

### Post by Allen_Emmanuel_P._ on 2016-01-06
(new to squid proxy server)

How do you block audio/video streaming with squid? I want people to access that certain website, but if they view/play the audio/video then it wotn run. 

I cant seem to block youtube videos using flash blocking. I just found out that youtube is now using html5 as player.

---

### Post by slickymaster on 2016-01-06
*Moved to the ***Security**[I] sub-forum

[/I]There are many example configurations available on the [Squid Proxy Wiki]("http://wiki.squid-cache.org/")
[Squid Web Proxy Wiki Blocking Media Streams]("http://wiki.squid-cache.org/ConfigExamples/Streams/Other")
[Blocking content based on MimeTypes Example: blocking flash video]("http://wiki.squid-cache.org/ConfigExamples/BlockingMimeTypes?highlight=%28ConfigExamples%2FIntercept%29%7C%28ConfigExamples%2FAuthenticate%29%7C%28ConfigExamples%2FChat%29%7C%28ConfigExamples%2FStreams%29%7C%28ConfigExamples%2FReverse%29%7C%28ConfigExamples%2FStrange%29%7C%28ConfigExamples%2FExtreme%29%7C%28ConfigExamples%2FPortal%29%7C%28ConfigExamples%2FSmp%29")

---

### Post by ajgreeny on 2016-01-06
If using firefox there is an add-on called **[flashblock]("https://addons.mozilla.org/en-US/firefox/addon/flashblock/?src=ss")** which has the option to block html5 as well as flash; I don't think the chromium version has that option.

---

### Post by maxinstuff2 on 2016-01-18
> **Allen_Emmanuel_P._ said:**
> (new to squid proxy server)

How do you block audio/video streaming with squid? I want people to access that certain website, but if they view/play the audio/video then it wotn run. 

I cant seem to block youtube videos using flash blocking. I just found out that youtube is now using html5 as player.

I'm not sure if that's possible without configuring the browser locally, it might be easier to just throttle all the youtube traffic. So the video will load but very, very slowly and trying to stream something from youtube would be a futile excercise.

---

