---
title: "About VirtualBox resolution"
date: 2007-08-09
forum: Virtualisation
---

### Post by gamerguy on 2007-08-09
Hi,
Just installed windows XP pro as the guest OS on my ubuntu linux 7.04. i'm using virtualbox here.

it works beautifully, but there's just one problem. my notebook LCD resolution is 1280 X 800, and i've managed to set my windows xp resolution in virtualbox to 1280X800. however, the start menu and taskbar is hidden below the screen, probably because the ubuntu taskbar at the top of the screen is eating away part of the screen that win xp is supposed to take.

how may i resolve this problem?

---

### Post by asmoore82 on 2007-08-09
have you tried making the VBox fullscreen (Hostkey+F) ?

---

### Post by gamerguy on 2007-08-10
yup, i did.
however, i still see the Linux taskbar at the top even after i've gone to full screen mode. and because of that, my windows taskbar at the bottom is obscured.
how do i make it go to "true" full screen mode ie. such that there's no hint that linux is in the background?
thanks :)

---

### Post by Seisen on 2007-08-10
You need to hide both of your taskbars in Ubuntu and  make sure that you hide them before you run VirtualBox otherwise you get a black strip, at least on my computer it did that. To hide them all you have to do is right click on the taskbar and select properties and thier should be an option to enable you to hide the taskbar.

---

### Post by emwine on 2007-08-24
I had this exact problem.  Turning off Desktop Effects (System->Preferences->Desktop Effects) solved it.  Hopefully this issue can be addressed eventually so that it won't be necessary anymore.

---

### Post by mk4umha on 2007-11-12
> **emwine said:**
> I had this exact problem.  Turning off Desktop Effects (System->Preferences->Desktop Effects) solved it.  Hopefully this issue can be addressed eventually so that it won't be necessary anymore.

Which desktop effects did you turn off?

---

### Post by emwine on 2007-11-30
> **mk4umha said:**
> Which desktop effects did you turn off?

I was running Feisty then.  The solution I described just disabled compiz, iirc.

But now on Gutsy, VirtualBox seems to be working [mostly] happily with all my desktop effects.  I think it's more because of the newer VirtualBox version, and not Gutsy so much.

---

### Post by sandwormblues on 2008-02-07
How did you manage to get 1200x800 resolution in virtualbox?  i don't have to modify the freakin' registry, do i?

---

### Post by hebetude on 2008-02-12
Not for novice, you're stuck in command line if you mess this up.

Open Terminal:
[Make a backup]
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
[Edit X11 config]
sudo gedit /etc/X11/xorg.conf

search for Screen

It looks like:
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        #Virtual    1280    1024
        Modes "1024x768@60"    "1280x960@60"    "800x600@60"    "1280x1024@60"    "640x480@60" 
    EndSubSection
EndSection

```

Add a new modes resolution by putting 1200x800 first in the mode definition.
```

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        #Virtual    1280    1024
        Modes "1200x800@60" "1024x768@60"    "1280x960@60"    "800x600@60"    "1280x1024@60"    "640x480@60" 
    EndSubSection
EndSection

```

The @60 isn't necessary, if yours doesn't contain that.

If your screen starts up black or buggered, fail-safe mode should activate.  If not, let it crash a few times then hit Ctrl+Alt+F1.  Login and overwrite your xorg.conf with the backup you created

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Good luck.

---

### Post by notaphish on 2008-02-21
If the question is how to appropriate your virtual XP box to be able to use more than just the standard 4:3 resolution ratios that come standard with the virtualization program's video drivers then the answer is different.
I don't know about virtualBox but in vmware server there is an option to have the guest OS fit to the winodw.  It basically makes the resolution automatically change based on what size it has to accomodate.  From here you can turn off the unnecessary toolbars and turn on "quick-switch" which hides the main toolbar and leaves you with your whole screen at a 16:9 ratio (assuming you are on a widescreen monitor) with only 2 or 3 pixels missing around the border.
Then if you are cool and have compiz box going you can press ctr+alt and then hold it and drag over to your other linux side.
If you want to shut down that OS just move the cursor to the top of the screen and the menu will pop back up and you can shut it down and get out of "quick-switch" mode.
:guitar:

---

### Post by fryser_d on 2009-03-13
[SOLVED]

I had the same problem, I solved it by pressing:

[Host+F] to get out of Fullscreen, then
[Host+G] To resize at my desktop size.
[Host+F] Then Fullscreen again.

That stupid, that simple XD :popcorn:

---

### Post by vex21 on 2009-10-10
> **fryser_d said:**
> [SOLVED]

I had the same problem, I solved it by pressing:

[Host+F] to get out of Fullscreen, then
[Host+G] To resize at my desktop size.
[Host+F] Then Fullscreen again.

That stupid, that simple XD :popcorn:
 Thanks, this helped. It was just as simple as you said, but worked only after I had installed Guest Additions. Took me some time to figure it out so I thought it worth mentioning it here.

---

### Post by wanna_try on 2009-10-16
Thanks, this helped!

---

### Post by markackerman8@gmail.com on 2010-04-13
Worked for me Thanks.

---

