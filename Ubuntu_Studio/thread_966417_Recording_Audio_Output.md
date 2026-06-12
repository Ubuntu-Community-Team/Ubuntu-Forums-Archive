---
title: "Recording Audio Output"
date: 2008-11-01
forum: Ubuntu Studio
---

### Post by Patrick793 on 2008-11-01
Hi everyone.

I need some help. On my Acer Aspire 5315, I can't record output.
I make tutorials for LMMS, and they aren't really helpful without sound. On my Desktop, I would choose mix, but I don't have this option.

Is there anyway I can record audio output on this?

Attached are screenshots of my tabs in Volume Control.

---

### Post by babarosa on 2008-11-01
Hi Patrick793,

if LMMS works with jack/qjackctl then try the following shown in the linked picture (replace mplayer-application with LMMS):

[http://www.servimg.com/image_preview.php?i=1&u=12842335](http://www.servimg.com/image_preview.php?i=1&u=12842335)

Audacity-Setup: [http://www.servimg.com/image_preview.php?i=3&u=12842335](http://www.servimg.com/image_preview.php?i=3&u=12842335)

Regards,
Michael

---

### Post by neu2buntu on 2008-12-27
yeah qjackctl is the way to go ....i have made a couple of demos on youtube of lmms ...i tried everything but to record the actual sound of lmms you need qjackctl....open >sound and video >jack control first,and start(you may need to change the default settings too,just google around for info on that) and have lmms audio driver as jack(needs a restart) and using gtk-recordmydesktop in sound settings tick jack for capture.....start recording and save.....just install these programs if you already do not have them..ok

---

### Post by neu2buntu on 2008-12-27
go here to see my vids of lmms... [http://uk.youtube.com/user/chrissymcmanus](http://uk.youtube.com/user/chrissymcmanus)

---

