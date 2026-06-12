---
title: "Importing HDV30 from Canon via 1394"
date: 2009-09-11
forum: Ubuntu Studio
---

### Post by RedRat on 2009-09-11
I have a Canon Vixia HD30 camera and my tapes are all in HDV30 format. I have tried to import these fies via capture in LiVES, Kdenlive, and others. Non seem able to see or capture these files. LiVES does have a provision in the menu for HDV, presumably Hi-Def video. 

Any ideas about encoders or decoders needed to be able to do this?? Any help would be appreciated.

---

### Post by cotcot on 2009-09-13
[[COLOR="Red"]dvgrab[/COLOR]]("http://www.kinodv.org/article/archive/7/") 3.5 is out and announces an automtic detection of HDV.  Kino (version 1.3.4 is the latest) is a video editor that gives you a UI for dvgrab.

I could not try it because I do not have an HDV camera.

---

### Post by RedRat on 2009-09-14
> **cotcot said:**
> [[COLOR=Red]dvgrab[/COLOR]]("http://www.kinodv.org/article/archive/7/") 3.5 is out and announces an automtic detection of HDV.  Kino (version 1.3.4 is the latest) is a video editor that gives you a UI for dvgrab.

I could not try it because I do not have an HDV camera.
Thanks for your reply. I downloaded dvgrab and had to compile it and install it. That went very well. The first time I have downloaded a tar file and actually did an install that way. Learned a great deal in doing that.

However, my attempts to download the latest version of Kino (1.3.4) did not go well at all. It failed to install. Now this may well be that was and is due to my use of Ubuntu 8.04 since it calls for some libraries that are just not available for Hardy. The last version I could install is 1.3.2, but trying that with dvgrab 3.5 still does not capture HDV. I will try some manipulation of dvgrab from the command line but I have pretty much given up on kino 1.3.4. Maybe someone out there has some suggestions, but I suspect that I must compile it under Jaunty or Karmic. 

For the time being, I can download the video via Adobe Premier under windows and then move the files to my Linux machine. 

If nothing else, this got me off my backside to try command line compiling and installing:)

---

### Post by RedRat on 2009-09-14
> **cotcot said:**
> [[COLOR=Red]dvgrab[/COLOR]]("http://www.kinodv.org/article/archive/7/") 3.5 is out and announces an automtic detection of HDV.  Kino (version 1.3.4 is the latest) is a video editor that gives you a UI for dvgrab.

I could not try it because I do not have an HDV camera.
OK, tried the command line dvgrab for capturing HDV from my camera, it works! dvgrab does indeed capture HD video and puts it into a file. Of course, being HD, the files are huge, but that is the nature of HD, I guess. 

The odd thing is that these files can be viewed in VLC and Kino and other editing software, e.g., kino 1.3.2! Strange that they can't capture via dvgrab. But that is the way of the world, I guess.

---

