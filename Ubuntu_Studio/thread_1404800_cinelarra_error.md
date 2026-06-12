---
title: "cinelarra error"
date: 2010-02-11
forum: Ubuntu Studio
---

### Post by zander1013 on 2010-02-11
hi,

running ubuntu 9.10...

i am getting this error when i try to play a .mov in cinelarra... "virtual int FileMOV::read_frame(VFrame*):quicktime_read_frame/quicktime_decode_video failed,result:" in a popup dialog box.

and there is only some scratch sound as the .mov plays slowly.

i am trying to change from oss to alsa sound but the accept button is displayed off the bottom of the screan. i cannot resize or move to click the accept change button.

please advise.

thank you.

---

### Post by cotcot on 2010-02-13
Maybe a codec problem. Can you open the .mov in other video editors without errors ?

---

### Post by zander1013 on 2010-02-13
> **cotcot said:**
> Maybe a codec problem. Can you open the .mov in other video editors without errors ?

yes. it plays fine in kdenlive running on fedora 12. i could not get kdenlive to work on ubuntu without the scratchy sound either.

---

### Post by LuridCinema on 2010-02-13
it sounds like you do not have the audio library / codecs installed...

have you installed all the libraries located at :
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)    ???

---

### Post by zander1013 on 2010-02-14
> **LuridCinema said:**
> it sounds like you do not have the audio library / codecs installed...

have you installed all the libraries located at :
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)    ???

that tutorial is how i got the media stuff going to begin with. and i install all the up dates.

i wonder if perhaps its because i am running on a laptop. but because kdenlive works well on the same hardware run by fedora 12 i am reluctant to blame the hardware (or lack there of).

cinlarra does not work well in fedora 12 either. mainly it breaks a bunch of packages to install it that can't seem to be repaired.

perhaps i will look into yellow dog linux. i have not tried to install that before and i have heard its a good distro but i am not giving up on ubuntu or fedora yet. :popcorn:

---

