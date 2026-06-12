---
title: "How to convert video dynamically"
date: 2009-09-23
forum: Ubuntu Studio
---

### Post by zelalem on 2009-09-23
Hi, I am thinking of using a tool to convert videos dynamically based on a user's request. So, if the user device supports a given codec I want the file to be converted into that format and be streamed. But, I don't want the user to wait while I convert the video file into anotehr file and then stream it to him/her. Basically I want to get the output of teh convertion to be streamed into network socket instead of file and want to do it dynamically. Is it possible to use ffmpeg to do this? 

Thank you.

Best regards,

Zelalem

---

### Post by FakeOutdoorsman on 2009-09-23
You might be able to do this with an mpeg2 steam, but I'm not too familiar with streaming and I've never used FFserver.  You would also need adequate hardware to decode the input and encode the output faster than real-time viewing.  This would be a good question for the [ffmpeg-user](http://ffmpeg.org/contact.html) mailing list or the #ffmpeg IRC channel.

---

### Post by sedawk on 2009-09-24
I never tried this myself, but I would assume that this
is some basic functionality of every (good) streaming
server (the file format the file is stored in doesn't
have to be the format inside the stream).

Have you checked out what VLC can do out-of-the-box?

---

### Post by zelalem on 2009-09-25
Thank you FakeOutdoorsman, I will post my question to that group. 

Hi Sedawk, I use VLC but it requires a specific format to stream a video. That is, you need to load the video (create a channel) before a request comes. So, I just assumed that it may not do it and thought FFmpeg could be the right solution. But I'll check out with VLC.

Thank you again for your help.

Best regards,

Zelalem

---

