---
title: "Youtube'ish website"
date: 2008-02-20
forum: Server Platforms
---

### Post by bstan2 on 2008-02-20
I am not sure if this is the correct place to post this, but here is what I am looking for:

1.  Ability to upload AVI or MPEG videos
2.  Convert the videos to FLV
3.  Have them show up on a webpage ready to view.

Are there any combination of programs that will do this?

Thanks all!

This will be an ubuntu 7.10 server running Apache and PHP and whatever else I need.

---

### Post by FakeOutdoorsman on 2008-02-20
I'm currently doing something similar, but on a CentOS box. This should point you in the right direction.  Let me know how it goes.

[Build Your Own Video Community With Lighttpd And FlowPlayer (Debian Etch)]("http://www.howtoforge.com/video_streaming_lighttpd_flowplayer")

---

### Post by jamescorbett on 2008-02-22
I wrote a PHP script that will work Apache as long as PHP safe mode is off, wine is used but if you can install mplayer (mencoder) then edit the PHP script a little it should work fine.

Basically; Upload, Automatically Encodes, HTML Script for embed.

Good Luck

[http://wve.sourceforge.net/](http://wve.sourceforge.net/)

---

