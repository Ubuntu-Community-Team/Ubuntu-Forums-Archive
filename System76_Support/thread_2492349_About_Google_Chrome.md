---
title: "About Google Chrome"
date: 2023-11-08
forum: System76 Support
---

### Post by wilienz on 2023-11-08
Hello everyone, there is a video on a website that I can play normally on Windows, but the video on the website cannot be played on the Ubuntu system. what should I do? Can this be solved with a Google Chrome extension?

---

### Post by TheFu on 2023-11-08
What video codec does the video use?
Is there any DRM involved? If so, which method/tool is used?  Some DRM is MS-Windows-only.

---

### Post by wilienz on 2023-11-08
I don't know, but the relevant personnel of the company told me that the video needs to be encoded, or there is no video decoder

---

### Post by SeijiSensei on 2023-11-08
Have you tried another browser like Firefox?

---

### Post by wilienz on 2023-11-08
Firefox will show that the video format and MIME type were not found

---

### Post by ajgreeny on 2023-11-09
Perhaps a link to that video, assuming that its content is acceptable to both you and this forum, might allow us to solve this more easily.
So far all we know is that it is a video.

---

### Post by TheFu on 2023-11-09
> **wilienz said:**
> I don't know, but the relevant personnel of the company told me that the video needs to be encoded, or there is no video decoder

Does ffmpeg know what it is?
Will mpv play it?
Will VLC play it?

Both those players can handle specific video URLs.

---

### Post by SeijiSensei on 2023-11-09
We're all spinning our wheels if you can't provide a link to the video.

---

### Post by wilienz on 2023-11-09
[https://wrraw-1309107969.cos.ap-guangzhou.myqcloud.com/welabel_cutbag/test/output_265_fast.mp4](https://wrraw-1309107969.cos.ap-guangzhou.myqcloud.com/welabel_cutbag/test/output_265_fast.mp4) &#65292;This connection is a video link, but it seems that it cannot be accessed through the external network environment.

---

### Post by SeijiSensei on 2023-11-10
Yup, that's no help.

At least we learned that it's an MP4 file. I've distributed mp4 files to a wide variety of viewers on wildly different platforms. I always encode with H.264 for video and AAC for audio. Works pretty much everywhere and across all browsers.

---

### Post by TheFu on 2023-11-10
mp4 is just a container. It doesn't provide the specific codec for video or audio.  If the file is only available where we cannot access it, then we will not be much help.

Did you do what post #7 says?  What were the results?

---

### Post by ajgreeny on 2023-11-10
The link you provided which I have downloaded to try is not an mp4 file at all.

According to command **file** it is an **XML 1.0 document, ASCII text of 445 bytes**. Not surprisingly it will not play as a video!

---

### Post by VMC on 2023-11-11
I'm havinf trouble locating that website "https://wrraw, etc,etc"

Maybe supply the web site info that points to this video.
Searching "wrraw" brings up nothing of value

---

### Post by ajgreeny on 2023-11-11
I right clicked the link and chose **Save as** which will normally save the video or audio if the link actually ends in the file suffix, eg, mp4 or mp3 etc.

If I simply left click on the link to open it, it goes nowhere.

---

