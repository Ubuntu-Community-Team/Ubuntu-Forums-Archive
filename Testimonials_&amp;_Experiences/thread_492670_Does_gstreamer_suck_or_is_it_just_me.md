---
title: "Does gstreamer suck or is it just me ?"
date: 2007-07-05
forum: Testimonials &amp; Experiences
---

### Post by Talon2 on 2007-07-05
I have been battling Ubuntu in an effort to be able to watch DVD's for some time.  I've searched and tried all sorts of things.  I've tried vlc, mplayer and a lot of tweaks.  What finally worked is blowing gstreamer away and installing xine.  The difference is astounding.

Can anyone tell me why gstreamer is the default in Ubuntu?

As far as I'm concerned gstreamer is trash.

---

### Post by ausmuso on 2007-07-05
You're not the only one, Talon2.
Yesterday I replaced my Totem-Gstreamer with Totem-Xine and it's been bliss for me ever since!

---

### Post by Talon2 on 2007-07-05
> **ausmuso said:**
> You're not the only one, Talon2.
Yesterday I replaced my Totem-Gstreamer with Totem-Xine and it's been bliss for me ever since!

Yes, bliss is a good way to describe dvd playing once xine replaces gstreamer.  I could also use the phrase "Just Works".  Using gstreamer didn't show one or two problems but rather a steady stream of them.

I'm sure there is a reason why gstreamer is in Ubuntu.  I really do wish someone would explain it because it certainly isn't obvious to me.

---

### Post by 3rdalbum on 2007-07-05
With Gstreamer, you can buy legal codecs for WMV, Mpeg, and all that sort of jazz. Those Gstreamer plugins won't work with Xine or any other backend. And Gstreamer is a requirement for a fairly large amount of software these days.

Besides, you don't need to get rid of Gstreamer. Just don't use Totem for DVDs. VLC works fine even when you have Totem-Gstreamer installed.

---

### Post by Talon2 on 2007-07-05
> **3rdalbum said:**
> With Gstreamer, you can buy legal codecs for WMV, Mpeg, and all that sort of jazz. Those Gstreamer plugins won't work with Xine or any other backend. And Gstreamer is a requirement for a fairly large amount of software these days.

Besides, you don't need to get rid of Gstreamer. Just don't use Totem for DVDs. VLC works fine even when you have Totem-Gstreamer installed.

VLC did not work well here.  The only solutions that I have found to play DVD's to my expectations are:

1) Totem - xine
2) xine-ui - xine

Maybe there is an issue with my hardware.  I run a ati 9600 graphics card using the open source driver.

---

### Post by rye_ on 2007-07-06
I'd also vote for vlc player.

Could  you clarify a little more (for interest rather than me being able to explicitly offer a solution)
the problems you experienced with totem-gstreamer or vlc.

also what's your graphics card?, I wonder if a unsuitable driver is the culprit?

Ryan

---

### Post by Talon2 on 2007-07-08
> **rye_ said:**
> 

Could  you clarify a little more (for interest rather than me being able to explicitly offer a solution)
the problems you experienced with totem-gstreamer or vlc.

also what's your graphics card?, I wonder if a unsuitable driver is the culprit?


There were many problems using Totem-gstreamer.  Here are a few:

- Putting a DVD in the drive would start video play but the controls in Totem would not.  I simply got an error code.

- Pause and play in Totem would not work.  If I tried to select pause then play would stop but it could not be started again.

- Unable to fast forward or select where to start play.

Once I install xine all controls in Totem worked fine and playback was great.  

The video card is a ATI 9600 using the open source driver.  Desktop effects works fine.  I tried video with and without desktop effects on.  Same problems.  Replacing gstreamer with xine caused everything to work exactly as expected.

---

### Post by ericnord on 2007-07-12
I'm having a lot of issues w/ VLC in Ubuntu as well. When I open a .VOB file the progress bar starts in the extreme right position (as if I'm at the end) and if I slide it to the beginning it just jumps back to the end. This is with a Dell Laptop using NVIDIA Quadro 512.

---

