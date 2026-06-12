---
title: "Ubuntu 13.04 Unity and Gnome performance differences"
date: 2013-05-10
forum: Ubuntu, Linux and OS Chat
---

### Post by dsana123 on 2013-05-10
Hi,

I've recently clean installed Gnome Ubuntu 13.04 after using 12.04.2 as I was interested in using Gnome 3. Functionally I prefer it to Unity (although I also like Unity), but noticed the following issues:

   * Switching between workspaces was not as smooth as Unity.
   * Screen tearing when playing videos.

I decided the issues were too annoying and cleaned installed Ubuntu 13.04 (with Unity), and the above issues disappeared so I intend to stick with Unity for the time being.

I am curious as to what the difference is between Unity and Gnome 3 that would account for this difference. Different compositing window managers or something else?

I am using a Sony Vaio VPCZ1 with a Core i5-540M CPU. I'm not using the nVidia GT330m discrete graphics (only the Intel integrated graphics).

Thanks.

---

### Post by mreq on 2013-05-10
I've been using Gnome, Unity and ended up on XFCE on my Z vaio. Before clean installing Xubuntu 13.04, I tried to play with Gnom and Unity again and was surprised, how **much slower** the overall response is (eg. the appearing of alt+tab switcher). I thought that Gnome and Unity were both running very smooth until I tried XFCE ;)

Video lagging is strange though. It should work well on any DE with your specs...

---

### Post by grahammechanical on 2013-05-11
Ubuntu Gnome is based upon Ubuntu which itself is based upon Gnome 3 desktop environment. Many of the Ubuntu utilities are actually Gnome utilities. Both distributions benefit from and are limited by what Gnome.org does and how well their development work goes. Ubuntu uses the Unity user interface. Ubuntu Gnome uses the Gnome 3 shell.

There are many developers working on Ubuntu. There are only a few (perhaps just a couple) working on Ubuntu Gnome. We should not think of Ubuntu Gnome as being developed by the Gnome Organisation. It is not. The drive on Ubuntu towards Ubuntu Touch will bring in many improvements to Unity. But not necessarily to Gnome 3 shell or Ubuntu Gnome, which should be thought of as a private initiative. 

Another thing we should figure in is the willingness, or lack of it, of the Gnome Organisation to merge patches from Ubuntu. The Ubuntu developers have the resources to patch Gnome code before it is merged into Ubuntu. This will also benefit Ubuntu Gnome but not the Gnome 3 shell part of it. Do the developers of Ubuntu Gnome have the resources to patch Gnome 3 shell or are they forced to wait until Gnome Organisation fixes things upstream?

In a way, we are not comparing like with like.

Regards.

---

### Post by markbl on 2013-05-12
My 2 cents of comment is that I have used GNOME Shell on Ubuntu 11.10, 12.04, 12.10, and now 13.04 as my primary desktop although I occasionally log in with Unity to see where it is at. I've always and still find that GNOME Shell performs more smoothly and with less glitches and better reliability than Unity. I have no problems with screen tearing etc. That is across both nvidia and intel video based systems. I like Unity but think GNOME Shell is better with a simpler but "beautiful" yet functional design.

---

### Post by Glynnux on 2013-05-14
I'm totally happy with Gnome Shell. I've used 12.04, 13.04 and currently settle for 12.10 either as Remix versions or the Ubuntu Gnome 13.04. I've only regressed to 12.10 as I need an up to date functional Google Earth. I've had no issues that weren't my own doing.
I did give 13.04 Unity a trial but there were delays with the operator (me) and I gave it up.
I do a lot of switching between applications and Gnome hot corner is a godsend for my brains way of working. Fully functional but in a visually sparse and beautiful way.
I use the "hide top bar" extension to allow me to access the resize function of Gimp (and the 'accept' and 'enter' buttons of some other software). This on my laptop with 1366x768 screen. On my main pc I don't need to hide the panel.

---

### Post by Jack Harper on 2013-05-15
I gave Gnome 3 a try on 13.04 and didnt like it much,performance was generally ok but it was laggy sometimes,and I didnt like the system fonts.I was a long time KDE user on Suse/OpenSuse,switched to Ubuntu and didnt like Gnome 2 much,Unity was a much better experience,especially since the improvements implemented in 13.04 and the addition of Unity Tweak Tool.Performs well,dash is very convenient,looks beautiful and clean,and what is important for me,system fonts on Unity look great,KDE and Gnome never seem to be able to achieve such clarity and sharpness of fonts no matter how much I tinker with them.At first Unity seemed clunky to me as a former KDE user but now its really slick and convenient.I am really looking forward to Unity on QT/QML.

---

### Post by markbl on 2013-05-15
> **Jack Harper said:**
> I gave Gnome 3 a try on 13.04 and ... I didnt like the system fonts. 
You are not clear here but presumably you installed the Ubuntu GNOME distro. I just do an "apt-get install gnome-shell" on top of a standard Ubuntu install and that gives me GNOME shell with the beautiful default Ubuntu Ambiance theme and fonts. I agree that the standard GNOME theme and fonts are ugly compared to this.

---

### Post by screaminj3sus on 2013-05-15
This should fix your screen tearing when watching videos in gnome-shell:

Add **CLUTTER_PAINT=disable-clipped-redraws:disable-culling**

to: **/etc/environment**

its a bug with gnome-shell's compositor, it doesn't do fullscreen redraws which causes tearing when used with intel and nvidia's drivers. Compiz does fullscreen redraws by default so it doesn't have this issue. The above workaround simply forces it to do full redraws instead of clipped redraws: [https://bugzilla.gnome.org/show_bug.cgi?id=669122](https://bugzilla.gnome.org/show_bug.cgi?id=669122)

The bug is "fixed", but it requires the buffer age extension to work which is not yet in mesa, so the workaround will be required until that extension is supported by the drivers.

---

### Post by dsana123 on 2013-05-16
@screaminj3sus: thanks for explaining the video tearing problem.

---

