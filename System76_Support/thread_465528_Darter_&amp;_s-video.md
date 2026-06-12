---
title: "Darter &amp; s-video"
date: 2007-06-05
forum: System76 Support
---

### Post by riseringseeker on 2007-06-05
I have tried to use my Darter with an s-video cable to be able to see DVD's on a Television set.  I of course have to hit Fn-F8 during the boot, but then it seems to come up - I see the Ubuntu logo and loading progress bar.  

When it is done though, it tells me there is an error with the X-server, and wants to know if I would like to try to fix it.  I did so once, having first backed up my xorg,conf, and it did not help - in fact I am very glad I had the back up.

If I respond "no" (I don't want to try to fix the X-server) I can get a CLI, and can do whatever I wish to with the command line.  Of course, the point of me doing this is to be able to see DVD's on a Television screen.

I posted the contents of my xorg.conf in another thread, but will post it again if needed.

---

### Post by thomasaaron on 2007-06-06
Check out this how-to:
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

It deals with the nVidia card, but the principles should be the same.

---

### Post by riseringseeker on 2007-06-09
> **thomasaaron said:**
> Check out this how-to:
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

It deals with the nVidia card, but the principles should be the same.

Actually, I read the ubuntu wiki and saw there was an updated driver for intel cards.  Installed it, and now s-video works - at least with the JVC TV I've tried it with.  The colors are not perfect, but it is usable.  I am guessing there is some tweaking that I can do to get the colors correct - will keep you posted.

---

