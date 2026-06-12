---
title: "Follow Screensaver Tutorial - Get Broken Image Always"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ewangr on 2012-04-13
Have followed the same tutorial that worked just fine on my installation on another computer, but on my newer computer the XScreensaver of GLSlideShow just keeps showing the same image even though I have pointed it to a USB disk that has gigs of JPGs. In my home directory I notice there is an errors file with the following:

```

(xscreensaver-demo:12662): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
compiz (decor) - Warn: failed to bind pixmap to texture
glslideshow: unable to load font "-*-helvetica-medium-r-normal-*-180-*", using "fixed"
Can't locate LWP/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/bin/xscreensaver-getimage-file line 53.
BEGIN failed--compilation aborted at /usr/bin/xscreensaver-getimage-file line 53.
Can't locate LWP/Simple.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.14.2 /usr/local/share/perl/5.14.2 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.14 /usr/share/perl/5.14 /usr/local/lib/site_perl .) at /usr/bin/xscreensaver-getimage-file line 53.

```

Does the above suggest anything I should be looking at?

---

### Post by ewangr on 2012-04-13
Not sure if I would call this "solved", but I installed the KDE-Screensavers package, and it evidently includes whatever the XScreensavers package was missing. So by installing KDE (even though I'm sticking with Unity), it makes the screensaver work.

It seems that it "should" be possible to find just the missing library rather than load about 200 megs of files, but perhaps I should just be happy it's working?

---

