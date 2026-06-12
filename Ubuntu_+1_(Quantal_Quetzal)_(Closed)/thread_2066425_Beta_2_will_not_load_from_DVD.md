---
title: "Beta 2 will not load from DVD"
date: 2012-10-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by unibroker on 2012-10-04
I just burned the iso this morning.  On loading I see the Ubuntu splash screen followed by artifact.  I then hear the logon screen bongos while still showing the artifact.  No further progress in loading.  After 4 attempts I decided to post here.  

Glad I settled on a Live CD.  The Ubuntu splash screen still shows the same resolution problems with my nvidia graphics chip that they had in June (that Live CD loaded without a hitch).  I didn't get to the desktop to see if it is changeable in Display Settings but then that is another challenge.

Thanks in advance.

---

### Post by mc4man on 2012-10-04
If you were to use the current daily likely all would be fine
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

With the beta 2 image - 
As soon as it starts booting press any key to go to options. Select lang, press enter, then on the Boot Options line remove - 
 splash
& then  proceed on to live session

---

### Post by tomdkat on 2012-10-04
> **mc4man said:**
> If you were to use the current daily likely all would be fine
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

With the beta 2 image - 
As soon as it starts booting press any key to go to options. Select lang, press enter, then on the Boot Options line remove - 
 splash
& then  proceed on to live sessionThanks for posting this. I'll give it a try.  I *just* booted an Ubuntu 12.10 beta2 (64-bit) live CD on a system with a nVidia GeForce 8600GT video card in it and was presented with an interesting black and white screen pattern. :)

I'll try the current daily image and see what happens.

Thanks!

Peace...

---

### Post by unibroker on 2012-10-04
> **mc4man said:**
> If you were to use the current daily likely all would be fine
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

With the beta 2 image - 
As soon as it starts booting press any key to go to options. Select lang, press enter, then on the Boot Options line remove - 
 splash
& then  proceed on to live session

Thanks for this response!  Keeps me from downloading again with my glorified dial-up.  Are you recommending to remove all of this ```
/initrd.lz quiet splash--
``` which is at the end of the Boot Options line?

---

### Post by mc4man on 2012-10-04
> **unibroker said:**
> Thanks for this response!  Keeps me from downloading again with my glorified dial-up.  Are you recommending to remove all of this  which is at the end of the Boot Options line?

```
/initrd.lz [COLOR="Blue"]quiet[/COLOR] [COLOR="Red"]splash[/COLOR]--
```

remove red (you can also remove blue if desired but not really necessary
The - - can stay though not sure if they matter

---

### Post by unibroker on 2012-10-04
> **mc4man said:**
> ```
/initrd.lz [COLOR="Blue"]quiet[/COLOR] [COLOR="Red"]splash[/COLOR]--
```

remove red (you can also remove blue if desired but not really necessary
The - - can stay though not sure if they matter

Worked this time.  I only removed "splash" the first time but for some reason it didn't work.  Resolution is perfect.  Thanks for your assistance.

---

