---
title: "Why is not this default?"
date: 2007-01-01
forum: The Cafe
---

### Post by Jimmy_r on 2007-01-01
Ok, Yesterday I installed Fedora Core 6.
Long story short: Ubuntu is back already(RPM and family did not like me, and the feeling was mutual), but:

One thing I was very impressed with in Fedora was that it was the first distribution to set my screen resolution to 1280x1024 by default.
Curious, I checked the xorg.conf file and was amazed that the lines were so few they fit on one screen.
Things like Resolution and refresh rates were completely left out.

So now back on Ubuntu, I tried this:
In normal cases, I must adjust the resolution and sync ranges in xorg.conf.

The xserver in Fedora was the same version(7.1) as in Edgy so I did this(If you have Edgy, you can try this)
Be sure you know how to restore the backup if the xserver do not start again.

```
cd /etc/X11/
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano xorg.conf
```

Now, this is the part in xorg.conf I changed:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection
```
I changed that part to this:

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV43 [GeForce 6600 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
        EndSubSection
EndSection
```

Saved, and did a ctrl-alt-backspace.

The XServer booted up in 1280X1024, the monitors native resolution.

So, by some strange reason the Ubuntu configuration system writes those lines for no reason, to owerwrite a good behavior(1280x1024) with a bad(1024x768 )

Is that a miss by the developers, or is there a reason for it?

Edit: I just find this amazing. I had cheat-sheet with my horizontal and vertical refresh rates...
Now I can just delete those lines from xorg.conf altogether, and it will Just Work :)

---

### Post by xmastree on 2007-01-01
Well, I'm not sure about the different depths, but the different resolutions ("1024x768" "800x600" "640x480") are the ones which it cycles through when you use Ctrl-Alt-Num+ or Num-

I guess without those it won't switch.

---

### Post by Jimmy_r on 2007-01-01
Hm, I tried that with the old xorg.conf, but it would not work anyway...
I found this while googling for it: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg134212.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg134212.html")

---

