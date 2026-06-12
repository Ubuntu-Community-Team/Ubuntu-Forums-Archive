---
title: "Setting up Video Sharing Website"
date: 2009-05-22
forum: Server Platforms
---

### Post by samurailink3 on 2009-05-22
Hey, all! I'm looking to build an almost youtube-like site for my own personal use for streaming video files to a web browser. Kind of like what sockso does for audio, I'm looking for video. I would like the ability to tell the server where my videos are stored then have it transcode them on-the-fly into a lighter (bandwidth) format, and then stream to a browser. Anyone know of a server package that does this?

I love what sockso does for audio, I'm just looking for that same type of solution for video.

Thanks for the suggestions! :D

---

### Post by Vegan on 2009-05-24
The simplest architecture is to simply make a folder under you web root and put the video files there and simply link them in a PHP/HTML/XML document.

You could also stuff the video into a SQL database and serve it from there, but that requires some programming.

If you are comfortable with programming in PHP, you can use the database angle, if not, use a simple HTML document.

---

### Post by samurailink3 on 2009-05-25
Yea, I thought about that, but the only problem I run into is that where this server is located, the upstream is less than satisfactory. I'd want to dynamically convert the files to a less bandwidth-intensive format, then transport.

---

