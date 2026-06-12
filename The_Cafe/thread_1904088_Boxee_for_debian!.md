---
title: "Boxee for debian!"
date: 2012-01-04
forum: The Cafe
---

### Post by sandyd on 2012-01-04
If youve been trying to build a debian HTPC with boxee, youve probably noticed that the dependencies don't work really well with debian.

Ive taken some time to fix them (their still the same packages), and added a few missing dependencies. Also stripped the deb repository

Note: [BOXEE 1.5 IS THE LAST VERSION FOR PC/MAC/LINUX.]("http://blog.boxee.tv/2011/12/26/boxee-1-5-fall-software-update/")

If your creating a long-term HTPC, and you want updates, I would advise that you use xbmc instead. Eden is almost done, and it works wonderfuly.

I couldn't use the x64 download links on the boxee site, so no x64 debs.

Debian Unstable
[http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb](http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb)
Run this (for safety's sake)after installing deb (only for debian unstable)
```

sudo ln -s /usr/lib/i386-linux-gnu/libGLEW.so.1.6 /usr/lib/i386-linux-gnu/libGLEW.so.1.5
sudo ln -s /usr/lib/i386-linux-gnu/libGLEW.so.1.6 /usr/lib/i386-linux-gnu/libGLEW.so.1.5.0

```Debian Stable
[http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb](http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb)

Edit: In case the BGP routes on my routers decide to die again, 
[http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb](http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb)
[http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb](http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb)

---

### Post by thatguruguy on 2012-01-04
> **sandyd said:**
> If youve been trying to build a debian HTPC with boxee, youve probably noticed that the dependencies don't work really well with debian.

Ive taken some time to fix them (their still the same packages), and added a few missing dependencies. Also stripped the deb repository

Note: [BOXEE 1.5 IS THE LAST VERSION FOR PC/MAC/LINUX.]("http://blog.boxee.tv/2011/12/26/boxee-1-5-fall-software-update/")

If your creating a long-term HTPC, and you want updates, I would advise that you use xbmc instead. Eden is almost, and it works wonderfuly.

I couldn't use the x64 download links on the boxee site, so no x64 debs.

Debian Unstable
[http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb](http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb)
Run this (for safety's sake)after installing deb (only for debian unstable)
```

sudo ln -s /usr/lib/i386-linux-gnu/libGLEW.so.1.6 /usr/lib/i386-linux-gnu/libGLEW.so.1.5
sudo ln -s /usr/lib/i386-linux-gnu/libGLEW.so.1.6 /usr/lib/i386-linux-gnu/libGLEW.so.1.5.0

```Debian Stable
[http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb](http://dl.sandyd.me/boxee-fixed/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb)

Edit: In case the BGP routes on my routers decide to die again, 
[http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb](http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb)
[http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb](http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-unstable.deb)

Although possibly helpful, your guide is a little late.

According to [this]("http://blog.boxee.tv/2011/12/26/boxee-1-5-fall-software-update/"), the Boxee devs have issued a warm "Go %*$@ yourselves" to their PC/Mac/Linux users. Boxee will no longer be supported for PC/Mac/Linux after the end of January.

---

### Post by BrokenKingpin on 2012-01-04
I tied Boxee in the past on my media center, and I liked it, but was too buggy and unstable. They also only seem to be focusing on the Boxee Box, as I have not seen a PC version released in quite some time.

Because of this I went back to XBMC, which is working pretty nicely.

---

### Post by Woodwa on 2012-02-21
Looks like I got it to work in 10.10 maverick meerkat
I had to install enca 1st..
```
wget http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb
sudo apt-get install enca
sudo dpkg -i http://dl.dropbox.com/u/3593659/fixed_boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb
```

and My 0.9 lirc mappings still work!

and the ABC iView App still is there..

I can't play video on iView... I'm going back to 0.9... or xbmc...

---

### Post by mips on 2012-02-21
I would just go the [OpenELEC]("http://www.google.co.za/url?sa=t&rct=j&q=openelec&source=web&cd=1&ved=0CC0QFjAA&url=http%3A%2F%2Fwww.openelec.tv%2F&ei=tsZDT9I2i5eFB-b4zNQF&usg=AFQjCNHoTR2gIG10uCmBVh8FnD_3QNH06Q") route.

[http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience](http://mybroadband.co.za/vb/showthread.php/376752-A-Complete-Guide-to-creating-the-Ultimate-TV-Experience)



.

---

### Post by moxen93 on 2012-08-17
Thank you for the message via email (info is interesting for everyone):

[INDENT][I]Hmm..
A few months after I posted the file, my server had a few infrastucture changes, and the download mirror was disconnected.

Try [http://oc.sandyd.me/public.php?service=files&token=f3ab09f38d5eff40570b1f4fb5648fdc13694084&file=/Software/boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb](http://oc.sandyd.me/public.php?service=files&token=f3ab09f38d5eff40570b1f4fb5648fdc13694084&file=/Software/boxee/boxee-1.5.0.23269-fab5dc5.i486.fixed-debian-stable.deb)[/I][/INDENT]

I could install boxee on squeeze though I had to upgrade "libstdc++6" to testing (including some dependencies)

---

### Post by BrokenKingpin on 2012-08-17
I actually picked up a boxee box recently and really like it. It is a shame they are not supporting it on the desktop anymore. It is not as customization as Xbmc, but the interface is really nice and has all the same basic features.

---

