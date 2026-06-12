---
title: "alsa doesn't recognize audio interface"
date: 2014-09-11
forum: Ubuntu Studio
---

### Post by makana2 on 2014-09-11
I am using a NI Komplete Audio 6 which is shows up in lsusb but doesnt show up in /proc/asound/cards and so, nothing else. Im a newbie and Ive been searching around the internet with no luck. Can anyone help? Thanks.

---

### Post by makana2 on 2014-09-12
Anybody have any clues?

---

### Post by jejeman on 2014-09-13
Guess it is not supported then.
Ask NI is the device class compliant.

---

### Post by JayPeeJay on 2014-09-24
I just recently go the KA6, it was really plug and play for me.  I'm not sure what your issue is, but I did my research before buying it, and yes, it is usb class compliant, and therefore fully functional out of the box in Linux.  The only thing remotely dicey for me was getting the s/pdif inputs to record (which is why I found this post).  I finally figured out that I have to use alsamixer in terminal to set the clock sync to external (that option isn't available to me in either the alsamixer gui or the gnome alsamixer app for some reason).  That being said I stricly use jack for all my audio production, so if you don't use jack maybe try it just as a means of trouble shooting.  In your jack setup under interface select hw:1 or whatever lsub reports for the KA6.  When you start up by default you should get 6 in and 6 out under connections.

---

### Post by makana2 on 2014-09-25
Thanks for the replies. Guess it's just one of those weird 1-off problems.

---

