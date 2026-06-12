---
title: "No sound on Gazelle Value gavz4 after Hardy 8.04 upgrade"
date: 2008-04-27
forum: System76 Support
---

### Post by pak33m on 2008-04-27
Hey everybody,

Tonight I upgraded my Gazelle Value gavz4 from Gutsy 7.10 to Hardy 8.04
and now I have no sound.  I've had this issue with previous upgrades but
was resolved by reinstalling the drivers.

This time when I went to install drivers using the System 76 Driver
2.2.0 a windows flashed real quick, I was promped with a message to
report a bug on Launchpad, reboot and no sound.  I repeated this a
couple of times with no success.

[RESOLVED] I did some research and finally found this
[http://sudan.ubuntuforums.com/showthread.php?t=703966](http://sudan.ubuntuforums.com/showthread.php?t=703966)  I did what the
guy in the last post suggested which was to enable the External Amp and
uncheck it.  And like he said  - viaola, sound! I don't think that I've
ever seen Extrnal Amp in the switches and I'm positive that I never
cheked it even if it was there al lthis time.

I was able to correct the problem but I thought that I would inlcude
some extra info that I used from other bugs that might be of some help:

I ran system76-driver in the terminal and received the following:

```
$ sudo system76-driver
grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
grep: /opt/system76/model/model: No such file or directory
python: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
```

Attached is alsa_installed.txt for your review.

I created a bug for it [https://bugs.launchpad.net/bugs/222919](https://bugs.launchpad.net/bugs/222919)

That's it.

Thanks,

Jimmy (pak33m)

---

### Post by porschify on 2008-04-28
What worked for me was double clicking the speaker in the top right hand corner, then clicking on the switches tab, then unchecking the external amp check box.  It seemed to be something that was checked default when I upgraded to 8.04 on my gazv4.  Hope that helps.

---

### Post by IgnacioMiller on 2008-05-04
OP's solution worked for me on my gazv4 running Ubuntu 8.04.

---

### Post by karlakompiles on 2008-06-08
Hi, I am also having sound issues with the Gazelle with Hardy 8.04.  I'm new; hopefully this is an OK place to post this question.

I did not have sound when coming back from suspend.  From an achieved forum, I learned to add this to fix the problem:

> 
options snd-hda-intel model=toshiba
...at the very end of /etc/modprobe.d/alsa-base.

This gives me sound after suspend.  However, about 1 time in 4, it gives a *deafeningly* loud beep for about 10 seconds when I try to resume.  Does anyone know what may be causing this problem?

Thanks!

---

### Post by thomasaaron on 2008-06-09
Try going to System > Preferences > Power Management > General
and de-select "Use sound to notify in event of error."

Also try System > Preferences > Sound > System Beep, and de-select
"Enable System Beep."

Hopefully one of those two will do the trick.

---

### Post by karlakompiles on 2008-06-09
Thanks, that worked!

Do you know why an error beep would be triggered?  It seems to suspend/resume just fine...

---

### Post by thomasaaron on 2008-06-09
I'm not really sure. If you want to post the output of...

> cat /var/log/messages > ~/Desktop/messages.txt

...after resuming, we can have a look and see if there was some error involved. But it's probably just be a little quirk of some kind.

---

