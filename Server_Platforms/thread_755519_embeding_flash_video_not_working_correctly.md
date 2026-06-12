---
title: "embeding flash video not working correctly"
date: 2008-04-14
forum: Server Platforms
---

### Post by jerome1232 on 2008-04-14
okay I have apache2 running as a webserver
I'm trying to embed a locally stored flash video into the webpage. My embed code looks like:
```
<object width="425" height="355">
<param name="movie" value="a7x_scream.flv">
</param>
<param name="wmode" value="transparent">
</param>
<embed src="a7x_scream.flv" type="application/x-shockwave-flash" wmode="transparent" width="425" height="355">
</embed>
</object>
```When I load the page there is a completely empty flash object there (i right  click the white area and i get a flash menu) but no video.

If I embed some code from youtube.com it will load and play the you tube file just fine.

My flash file plays as a flash file unber mplayer just fine.

Any help or a link to a guide maybe would be greatly appreciated, I haven't found anything useful myself yet.

EDIT: on researching I need an FLVplayer on my websever, i'm unsure how to get one properly installed

---

