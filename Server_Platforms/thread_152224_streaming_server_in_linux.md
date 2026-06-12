---
title: "streaming server in linux"
date: 2006-03-29
forum: Server Platforms
---

### Post by M4av0 on 2006-03-29
Hi all,
I want to setup a (true/live) streaming server on my ubuntu box. There is some info 
I've found on the net about it. But I would like to know if any1 has any experience 
with this stuff and what is the best way to go. Btw: I'm thinking about using IP 
cameras (can this work?). Thanks for your help!

---

### Post by encompass on 2006-03-29
well if you use an IP camera... you can re route the data... but many times just plugging it in a fowrarding a few ports will get you running... I currently runa webcam for personal use and can have about 5 people see my cam at 1 a sec.  Wasn't too hard to se up... I will be doing the same settup for a radio station in wisconsin.

---

### Post by echo $USER on 2006-03-29
"sudo apt-get install gnump3d"  is a great audio streaming server and can run on any port that is free; it can also serve video but can not stream it.  vlc is a streaming video server that I am currentlytrying to figure out.  But it is frustrationg the **** out of me.

---

### Post by M4av0 on 2006-03-31
I also tried vlc. I think I configured it correctly, but I couldn't see any streams in Windows Media Player or WinAmp, I was only able to save file to disk. Then (amazingly) I found out that you need vlc media player to be able to watch it's streams. It figures :(. I still haven't come across a streaming server/player which would stream to other players than itself.

---

### Post by SteMMo on 2007-01-22
I'm testing vlc and it works ok with saved files.
How can i insert a webcam in this architecture ?

Thanks

---

### Post by elst on 2007-01-24
FWIW, Flumotion (in Universe) handles streaming from Webcams etc., and may be easier to set up. It's used to stream some OSS conferences.

---

### Post by ixus_123 on 2007-06-15
Did you find a solution that works?


I'm interested in doing this too. I need to make a server that can stream a monthly company meeting live over our intranet.


I've haven't made a start yet but have been googling for links so far I have:


Apple's Darwin Streaming server
[http://developer.apple.com/opensource/server/streaming/index.html]("http://developer.apple.com/opensource/server/streaming/index.html")
&
[http://www.linuxjournal.com/article/6720]("http://www.linuxjournal.com/article/6720")

The above mentioned Flumotion
[http://www.flumotion.net/documentation/]("http://www.flumotion.net/documentation/")

This tutoruial to stream ogg theora (which I'm not sure I understand
[http://mcs.hackitectura.net/tiki-index.php?page=live+stream+ogg+theora+ffmpeg2theora+oggfwd]("http://mcs.hackitectura.net/tiki-index.php?page=live+stream+ogg+theora+ffmpeg2theora+oggfwd")

Most promising looking - Theora streaming with icecast
[http://www.oddsock.org/guides/video.php]("http://www.oddsock.org/guides/video.php")

I've never done anything like this before & the budget I have for doing this is "as cheap as possible"

I like the idea of using theora because it's open. Using Darwin / mpeg involves licencing issues which are no doubt complicated.

It would be great to hear any updates on this thread. In the mean time I'm going to try and get a test server set up in VMware

---

### Post by SmallAxe on 2007-07-10
[QUOTE=ixus_123;2847568]Did you find a solution that works?


I'm interested in doing this too. I need to make a server that can stream a monthly company meeting live over our intranet.

.....Saw your  post 

 I would suggest using Vlc and Darwin streaming server because they can be fed to a quicktime player.

Also checkout StreamGuys.com, and contact me if you have any other questions or need furthur assistance

---

