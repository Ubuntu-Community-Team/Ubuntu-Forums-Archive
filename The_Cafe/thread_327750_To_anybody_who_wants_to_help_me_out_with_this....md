---
title: "To anybody who wants to help me out with this..."
date: 2006-12-29
forum: The Cafe
---

### Post by realwx on 2006-12-29
I've posted this in numerous forums and nobody has a solution, so I'm hoping a smart person can help me...

Let me explain the situation. If you've been on Digg, Fark or Slashdot then you know about Alek Komarnitsky's Internet Controllable Christmas Lights in helping to raise money for a cure for Celiac Disease. If not, a little Googling will help. Anyway, for the pity of trying to help the guy who wants a programmer to figure out how to stream the three D-Link 6620G webcams into three seperate servers (he's FTPing 3 images into 3 seperate servers every 3 seconds).

So far a little bit of source code findings point to a WMP-ish (not exactly) MPEG-4 stream with the extension .vam.

However, I can't figure out a way to actually stream the continuously streaming .vam video to his three servers. My friend keeps suggesting "port forwarding" but in theory that would just connect thousands of connections from one IP, whereas I need a program/solution where any packet of data that it receives is automatically uploaded to one of the three servers, where the thousands can connect and receive the packets, so essentially it is...

[img]http://www.siriusbackstage.com/forum/attachment.php?attachmentid=412&d=1167103778[/img]

In short.. I'm asking how to upload individual packets of data into the web server so that thousands of people can download the streaming packets into their own computers like in the image above.

---

### Post by RandomJoe on 2006-12-30
The first thing that came to mind while reading your post was [ZoneMinder]("http://www.zoneminder.com"), which is intended to monitor various cameras and provides a "security system" type display thru a web page.  It can also ship video clips out to another system for archival, and various other things.  Perhaps you could have the servers pull the video feed from a ZoneMinder system at the house, then reprocess that feed as needed for the web page?  (I'm not a web guru by any means...)

This isn't really "streaming video", but I get maybe 3-6 FPS out of my setup with my 3 cheapo D-Link IP cameras.  You can still watch people moving around and such.  In my case, the webcams do have a streaming output, but ZoneMinder doesn't (can't?) access it.  Instead, it is also possible to grab a .jpg image "snapshot" from the camera, and ZM uses that.  It just polls the cameras as fast as possible, giving me the mentioned rate.

The nice thing is you don't have to have any special software on the browser end to see it.

---

