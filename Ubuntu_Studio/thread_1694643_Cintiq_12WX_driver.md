---
title: "Cintiq 12WX driver?"
date: 2011-02-24
forum: Ubuntu Studio
---

### Post by thundaboom on 2011-02-24
Hey All,

I have recently bought a cintiq 12wx wacom graphics tablet, and it works fine on my Windows Box. However, I was wondering if it would be possible to integrate it with Ubuntu. I've looked around and I've found the [linuxwacom]("http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Main_Page") project, but it hasn't worked out for me. I extract their tar ball, run the installation as they told me too, and it does not work.

Has there been other kinds of Cintiq 12wx drivers for Ubuntu lately? That would really help if I would be able to use the Cintiq with it.

---

### Post by Favux on 2011-02-24
Hi thundaboom,

Cintiqs should work out of the box in Maverick.  Is the Cintiq 12wx a recently released model?  Or do you mean a Cintiq 12SWX?

Let's find the product ID by entering in a terminal:
```
lsusb
```
Post the Wacom line.

What exactly did you do from the linuxwacom project?

---

### Post by ragtag on 2011-02-24
I have the Cintiq 21ux running under 10.04 without any problems. I don't think I actually installed anything at all to get it up and running. You shouldn't need to custom compile or download anything directly from the linux wacom project. The 12wx may be different, but try entering the following in the terminal:

```
apt-cache search wacom
```

To see what packages are available that relate to wacom. I have 'xserver-xorg-input-wacom' installed, but I don't know if it's still in use in Maverick. To install it, enter:

```
sudo apt-get install xserver-xorg-input-wacom
```

In GIMP you can then go to Edit>Preferences, and Input Devices>Configure Extended Input Devices, and set the stylus and eraser mode to screen. Now you should have pressure support in GIMP. Check out MyPaint too, and InkScape, if you haven't already. :)

---

### Post by thundaboom on 2011-02-25
@Favux Thanks, that's actually the command i was looking for to check if it was recognised :D

@ragtag Oh wow, thank you so much! It works now, so I can finally use Inkscape. :3

Thanks for sorting this out.

---

### Post by juanochoa on 2011-08-08
Hello folks. Decided to migrate to linux a couple of days ago, loving every bit of it, except the hassle that's been getting my cintiq to work properly. The set input device to screen workaround isn quite there, because there is a mirror cursor floating to my left that decides if i'm working on the canvas or not. The lack of graphcial calibration is also driving me nuts. 
I don want to go back to win but deadlines loom and i'm starting to get scared!

---

### Post by Favux on 2011-08-08
Hi juanochoa,

Welcome to Ubuntu forums!

Which release of Ubuntu are you using?  Natty (11.04) etc.?
> The set input device to screen workaround isn quite there, because there is a mirror cursor floating to my left that decides if i'm working on the canvas or not.
That's a new one.  Are you talking about Gimp?

What's the output in a terminal of *xinput list* and *xsetwacom list*?

> The lack of graphical calibration is also driving me nuts. 
In Natty xinput-calibrator is in the Universe repository so just search for it.  For Lucid xinput_calibrator has a PPA:  [https://launchpad.net/~tias/+archive/xinput-calibrator-ppa](https://launchpad.net/~tias/+archive/xinput-calibrator-ppa)  Otherwise:  [http://www.freedesktop.org/wiki/Software/xinput_calibrator](http://www.freedesktop.org/wiki/Software/xinput_calibrator)

---

