---
title: "howto use onboard and usb soundcard as one?"
date: 2010-10-14
forum: Ubuntu Studio
---

### Post by marijus on 2010-10-14
hello,
i recently got a tascam US-122L usb sound device and it works very well in ubuntu maverick.

anyway, i'm wondering if it is possible to combine the onboard soundcard (Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)) with the usb sound device to have 4 independend outputs.

usecase: lets say i want to use ardour for a live performence and i'd need a stereo output for my loops and stuff (tascam) and another output for the click (onboard intel).

Is it some how possible to configure this in .alsarc or is there any other way?

any help appriciated!

regards, marijus

---

### Post by Pablo_F on 2010-10-14
Hi, you can try with alsa_out. Not sure if the sync will be good enough though.

man alsa_out

Cheers! Pablo

---

### Post by marijus on 2010-10-14
hey!

thanks for the hint...

i found this with a little googling alsa_out:

[http://www.backports.ubuntuforums.org/showpost.php?p=7093866&postcount=2](http://www.backports.ubuntuforums.org/showpost.php?p=7093866&postcount=2)

and it does exactly what i was looking for...
no problems with syncing so far!

---

