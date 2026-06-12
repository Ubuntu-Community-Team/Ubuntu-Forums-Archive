---
title: "I am stunned! The new radeonhd is great!"
date: 2008-08-18
forum: Testimonials &amp; Experiences
---

### Post by terrax on 2008-08-18
Hello everybody.

Just wanted to tell you how pleased I am with the new radeonhd driver.

I have an Asus M50SA with an Ati hd3650 gfx card. Have a lot of bugs using fglrx like; freeze when login out of kdm, wine screen distortion bug, wine direct3d bug and alot more with fglrx.

So I gave radeonhd a chance, though I know 3d support is a nogo yet, and I don't know about 2d.

When installed latest drm, dri, mesa and radeonhd driver and restarted X, I was sceptical, if it even started up.

But now I have a X session running with radenhd. Not with 3d support, but damn its fast in firefox and moving windows. There is no glitches when watching a movie. Maybe 2d support was included after all.

Thx AMD/Ati and radeonhd developers for this opensource driver. And I know it will be even better with time. :guitar:

---

### Post by terrax on 2008-08-18
BTW. If anyone is interested, I can tell you how to install this driver and my xorg.conf configuration.

---

### Post by sdennie on 2008-08-18
Moved to Testimonials forum.  Glad your new card is working.

---

### Post by Harvy on 2008-08-23
> **terrax said:**
> BTW. If anyone is interested, I can tell you how to install this driver and my xorg.conf configuration.

well, tell us please

---

### Post by Lamice on 2008-09-04
Hello terrax,
Congratulation on setting up radeonhd. By the way, can you share with me your xorg.conf file? Whenever I try to use radeonhd instead of fglrx, X would not start up. It reports "no screen can be found." Therefore, I have not been able to switch out of fglrx.
Thank you!

---

### Post by Crafty Kisses on 2008-09-05
Glad to hear everything is working out, any problems please post back. :)

---

### Post by Sef on 2008-09-05
> BTW. If anyone is interested, I can tell you how to install this driver and my xorg.conf configuration.

Just post details like that.  People will appreciate you for doing so.

---

### Post by terrax on 2008-09-14
Sorry I haven't been replying. I am busy with university now.

You have to follow this guide:
[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)
But I might make a new guide, because I had to pull the git version instead using the guide's repositories.

Also I had to make this option in xorg.conf
Under device section:
> 
Option "NoRandr" "yes"


Else my Xorg would startup with a black/grey screen.

---

### Post by terrax on 2008-09-14
> **Codename said:**
> Glad to hear everything is working out, any problems please post back. :)

As descriped in earlier reply, I have to make the NoRandr option in xorg.conf to be able to startup without a black/grey screen. I have filled a
_[[COLOR="Blue"]bug report[/COLOR]]("http://bugs.freedesktop.org/show_bug.cgi?id=16892")_, but it hasn't been reported fixed in git.

---

### Post by terrax on 2008-09-14
> **Lamice said:**
> Hello terrax,
Congratulation on setting up radeonhd. By the way, can you share with me your xorg.conf file? Whenever I try to use radeonhd instead of fglrx, X would not start up. It reports "no screen can be found." Therefore, I have not been able to switch out of fglrx.
Thank you!

Uhm did you pull the radeonhd source code from git? xorg.conf isn't really relevant I think, because the driver is designet to run without a xorg.conf I think. But my xorg.conf is in the bug report from the post before.

---

