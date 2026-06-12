---
title: "Youtube Downloader And Converter"
date: 2007-11-08
forum: Ubuntu Brainstorm
---

### Post by herculesthemad on 2007-11-08
I am currently developing a new program that downloads vids from youtube and converting them to any supported type from ffmpeg. i am writing it to mono c# with gui. i am wonderring if it could be in ubuntu repos.

thanksin advantage and sorry for my english or greeklish:)

---

### Post by 23meg on 2007-11-08
If it's [licensed suitably]("http://www.debian.org/social_contract#guidelines"), and someone does the packaging work, of course it can. Is the code available anywhere?

---

### Post by stinger30au on 2007-11-08
dont know if this website will help you or not

[http://youtubedownloader.org/](http://youtubedownloader.org/)

---

### Post by spanella47 on 2007-11-08
May look at and work with the people at Miro.  already has the ability to download from YouTube and would profit across the board from having the ability to convert between formats.

---

### Post by pay on 2007-11-08
Theres also youtube-dl [http://www.arrakis.es/~rggi3/youtube-dl/](http://www.arrakis.es/~rggi3/youtube-dl/) that copies the file to the computer but it doesn't convert or anything.

---

### Post by teasum on 2007-11-08
I would recommend polishing and packaging QtTube to address this need: 

[https://wiki.ubuntu.com/QtTube]("https://wiki.ubuntu.com/QtTube")

The interface is simple, it visually integrates well into Ubuntu, and I believe the latest version of it converts to .ogg, and possibly other formats.  Essentially, it is a frontend for youtube-dl, mentioned in the above post.  I have it installed through the more complicated process described in the linked page above, but if it were a package in the repositories, this tool would be widely used than either youtube-dl (via the command line) or the website mentioned above, I think.  Just my .02.

---

### Post by 23meg on 2007-11-08
Something else that may be of interest:

[http://arstechnica.com/journals/linux.ars/2007/10/16/using-youtubes-gdata-api-in-linux-desktop-applications](http://arstechnica.com/journals/linux.ars/2007/10/16/using-youtubes-gdata-api-in-linux-desktop-applications)

---

### Post by Turgon on 2007-11-08
Conduit can download (or sync) youtube videos as well and is wanted for also, so that might be the best way to get it into ubuntu.

---

### Post by thewOndErEr57 on 2008-05-16
Guys, in case people are looking for a GUI tool for downloading youtube videos in Linux, I've written a little software tool that does exactly that!

It uses the youtube-dl script, but also allows you to choose the desired format of the video, the resolution of the video and you can store which directory you want all of your videos to be stored to.

Find it here:

[http://yourtubedownloader.awardspace.com/]("http://yourtubedownloader.awardspace.com/")

Feedback most appreciated!

Thanks

---

### Post by LaRoza on 2008-05-16
Such tools are against the Youtube Terms of Use I think...

---

