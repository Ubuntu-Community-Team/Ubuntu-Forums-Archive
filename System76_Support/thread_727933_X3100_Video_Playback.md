---
title: "X3100 Video Playback"
date: 2008-03-18
forum: System76 Support
---

### Post by Aggrocrag on 2008-03-18
I'm a happy Daru2 owner, with Gutsy 32-bit, which has the Intel X3100 on it.

I went to install Compiz on it a while back, and found that one way to get it to work was to use XGL.  I don't remember the exact details, but I do know it slowed down the computer significantly.  So I got rid of it.  

When I decided I wanted to see If I could get it to work without XGL (which I did).  I got it working by closely following [http://knowledge76.com/index.php/GutsyCompizIntelX3100](http://knowledge76.com/index.php/GutsyCompizIntelX3100)

For the most part everything works, except playing video, despite following the part on the guide to re-enable video.  Changing the output to "X Window System (No Xv)" (or its equivalent not in gstreamer-properties, but rather in the media player, VLC.  I know it still doesn't work because the videos don't play in Mplayer.

I don't know if it is at all related, but I could the fact that I am using Xine at all effect anything. (I'm still learning all this stuff, so I'm not really sure what Xine and gstreamer are)

Is there anyway to correct this other than specifically going through my media players and changing the output?  I'm not too sure as to what it might effect in the future, so I'd rather avoid any troubles later.

---

### Post by thomasaaron on 2008-03-18
Xine is a pretty sweet player. It should play videos.
If you disable Desktop effects, do videos play? (System > Prefs > Appearance > Visual Effects > None)

Also, you might want to go ahead and just do a fresh install of Ubuntu 64-bit. It is working splendidly, and it will allow you to achieve S1 suspend with your DarU2.

---

### Post by theologian aaron on 2008-03-18
Did you change your video output to "X Window System (noXV)" in the multimedia systems selector, or just in VLC?  

I've had problems getting VLC to work properly, particularly with DVD's so i just dont use it.  I can play videos in mplayer and the totem movie player with no problems.

---

### Post by Aggrocrag on 2008-03-18
> **thomasaaron said:**
> Xine is a pretty sweet player. It should play videos.
If you disable Desktop effects, do videos play? (System > Prefs > Appearance > Visual Effects > None)

Also, you might want to go ahead and just do a fresh install of Ubuntu 64-bit. It is working splendidly, and it will allow you to achieve S1 suspend with your DarU2.

My mistake on one part, because videos play/don't play just like they do when compiz is on.  However, I do believe the problems started when I adjusted the settings to enable compiz.  

Also, I am starting to realize that it may not be too big a deal, as I intend to take a look at other OS's (Linux Mint, and another ubuntu-based distro called crunchbang).  I just want to get a look at everything, and I intend to either install 64bit Gutsy eventually, or 64bit Hardy when it comes out.  

Did you mean I might want to install 64bit Gutsy or the available version of 64bit Hardy?


> **theologian aaron said:**
> Did you change your video output to "X Window System (noXV)" in the multimedia systems selector, or just in VLC?  

I've had problems getting VLC to work properly, particularly with DVD's so i just dont use it.  I can play videos in mplayer and the totem movie player with no problems.

I went into the preferences in VLC and changed the Video Output Module to "X11 Video Output", after following the guide's instructions to change 'gstreamer-properties' to "X Window System (noXV)" had no effect.
Although I am guessing that our differences are perhaps occurring because I am using Xine.


Is it possible that the gstreamer-properties that the guide told me to adjust my video output to  "X Window System (noXV)" did not adjust Xine's output?

---

### Post by thomasaaron on 2008-03-18
I wouldn't install Hardy yet. I'd just do 64-bit Gutsy.
I can't really provide you with much support in Hardy yet, since we've not finished testing -- and won't until it is released near the end of April.

---

