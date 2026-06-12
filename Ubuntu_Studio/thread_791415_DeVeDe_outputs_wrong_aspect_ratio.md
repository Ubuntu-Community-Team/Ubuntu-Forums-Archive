---
title: "DeVeDe outputs wrong aspect ratio"
date: 2008-05-12
forum: Ubuntu Studio
---

### Post by bug80 on 2008-05-12
I'm trying to author a PAL DVD with DeVeDe:

I've made compliant MPEG files using ffmpeg. So far so good, the input and output files are both in 4:3 aspect ratio.

Next, I load the files in DeVeDe and tick the box "This file is already a DVD/xCD-suitable MPEG-PS file". DeVeDe opens the file and correctly reports the PAL resolution, and 4:3 aspect ratio.

BUT, if I let DeVeDe generate the DVD, the output video is in 16:9 aspect ratio! In other words, the video gets stretched horizontally.

Very strange...

Does someone know a solution? I do not want DeVeDe to transcode my files, because I get A/V sync problems on one of the videos if I do so.

[EDIT]
**Ok, I solved the problem.** It turns out that I have to add "-aspect 4:3" explicitly to the ffmpeg command line. This changes nothing to the video, but apparently ffmpeg sets some sort of flag which makes DeVeDe output the correct aspect ratio!
[/EDIT]

---

### Post by didac on 2008-05-12
It does it to me, I dunno why. My solution (yes, a long way):

Uncheck the box Remove temporary files when creating the DVD. I cannot remember the literal words. I'm in a computer without devede

Edit the .xml file. Go to where the aspect ratio is. Change it to 4:3. Then do

```
dvdauthor -x filename.xml -o dvdfolder
```

Now make the iso file

```
mkisofs -dvd-video -V My_DVD -o dvd.iso dvdfolder/
```

Burn dvd.iso

---

### Post by bug80 on 2008-05-13
> **didac said:**
> It does it to me, I dunno why. My solution (yes, a long way):

Uncheck the box Remove temporary files when creating the DVD. I cannot remember the literal words. I'm in a computer without devede

Edit the .xml file. Go to where the aspect ratio is. Change it to 4:3. Then do

```
dvdauthor -x filename.xml -o dvdfolder
```

Now make the iso file

```
mkisofs -dvd-video -V My_DVD -o dvd.iso dvdfolder/
```

Burn dvd.iso
Thanks for your reply! I solved the problem though, see my edit in the opening post.

---

### Post by didac on 2008-05-13
Thanks for your edit. By trying to help you, you helped me to solve my own problem. Now I know why it happened to me

---

