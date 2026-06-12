---
title: "I wrote a color picker applet"
date: 2007-02-11
forum: The Cafe
---

### Post by kegie on 2007-02-11
Hey there,

I wanted a little applet to sit in my panel to pick colors like ColorZilla but not depending on having firefox running, but couldn't find anything out there for gnome (I think there is something similar for KDE). So I decided to write it myself.

[IMG]http://www.undiscoverable.com/wp-content/picker_middleclick.jpg[/IMG]

For details, see my blog post about it [here]("http://www.undiscoverable.com/2007/02/11/color-picker-applet/"). To download it directly, [click here]("http://www.undiscoverable.com/wp-content/colorapplet-1.0.tar.bz2").

**Installation**
To install on edgy (the only distro I have tried it with), run 
```
./configure --prefix=/usr
```
followed by 
```
sudo make install
```
You may have to restart your gnome panel to get it to show up.

You need the prefix thing to get it to show up in the panel, otherwise gnome doesn't find it.

---

### Post by Nikron on 2007-02-11
Cool, I'll try it, but have you heard of gcolor2?


sudo apt-get install gcolor2

---

### Post by IYY on 2007-02-11
Very cool. I'll give it a try once the next version of XFCE comes out and I can use Gnome applets.

---

### Post by kegie on 2007-02-11
Nikron: Yeah, gcolor2 is great (but agave is better ;)), it doesn't do the gnome panel + recently used colors thing, which is what I wanted.

---

### Post by RAV TUX on 2007-02-11
> **kegie said:**
> Hey there,

I wanted a little applet to sit in my panel to pick colors like ColorZilla but not depending on having firefox running, but couldn't find anything out there for gnome (I think there is something similar for KDE). So I decided to write it myself.

[IMG]http://www.undiscoverable.com/wp-content/picker_middleclick.jpg[/IMG]

For details, see my blog post about it [here]("http://www.undiscoverable.com/2007/02/11/color-picker-applet/"). To download it directly, [click here]("http://www.undiscoverable.com/wp-content/colorapplet-1.0.tar.bz2").

**Installation**
To install on edgy (the only distro I have tried it with), run 
```
./configure --prefix=/usr
```followed by 
```
sudo make install
```You may have to restart your gnome panel to get it to show up.

You need the prefix thing to get it to show up in the panel, otherwise gnome doesn't find it.

Nice! Awesome work...reminds me of the Color Picker in KDE

[[IMG]http://img443.imageshack.us/img443/6607/snapshot24ln7.th.png[/IMG]]("http://img443.imageshack.us/my.php?image=snapshot24ln7.png")

---

### Post by Nikron on 2007-02-11
Mmm, I get this error when I try to .config

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

It shows I have the package in the manager though.

---

### Post by kegie on 2007-02-11
I have no clue when it comes to packaging and dependencies, it's on my list of things to figure out.. but I think that what you need are the packages **python-gtk2** and **python-gnome2**. It could be that you need the *-dev versions as well, but they shouldn't be necessary.

---

### Post by Nikron on 2007-02-12
Well, I compiled it, and now I can't find it in the the add to panel..

BTW, I had to installed the -dev and -1.2 versiosn of pygtk

---

### Post by kegie on 2007-02-13
It usually takes a little while for it to show up in the add to panel, for some reason. What you can do is log out and back in again, and it should be there.
If it isn't, it could be because you forgot to add --prefix=/usr to the ./configure call before calling sudo make install, that'd put it in the wrong place and the gnome panel won't find it..

---

### Post by Nikron on 2007-02-13
Got it working.. love it, thanks

---

### Post by kegie on 2007-02-13
Awesome. :)

---

### Post by beercz on 2007-02-13
> **kegie said:**
> I have no clue when it comes to packaging and dependencies, it's on my list of things to figure out.. but I think that what you need are the packages **python-gtk2** and **python-gnome2**. It could be that you need the *-dev versions as well, but they shouldn't be necessary.

Hi

Cool App btw - will use it a fair bit.  It wouldn't install for me until I installed **python-gtk2** and **python-gnome2** as you suggested.  I how have it running in the panel where the clock is (can't remember what it is called at the moment - aka the System Tray in Windows).

Well done and thanks.

---

