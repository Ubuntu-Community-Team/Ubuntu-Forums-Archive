---
title: "Suggest a gaming mouse?"
date: 2007-11-21
forum: Ubuntu Gamers Arena
---

### Post by Envy0pla on 2007-11-21
Hello there,  

I have been using Ubuntu for about 2 weeks now :D Got most things sorted except my mouse :( 

I have looked around and attempted tutorials, and forums and such re: how to get my mouse working under Ubuntu 7.10 and how to enable the side buttons but thus far in vain.

It is a Logitech bluetooth MX1000 Rasor,  I just can't seem to get it working.
I have tried installing bluetooth um....stuff via apt-get,   :P  and have had it going twice :D  but both times I could not get the side buttons working correctly...they did things,  but um..not what they used to do lol. and when I restarted it dissapeared again. 
I even got so desperate I attempted to use the setpoint software....it didnt go down well :P

I mainly play WOW but would like to play UT3 when it comes out, so I am thinking I might just buy another mouse :)  With a cord this time :) 

Can anyone out there suggest a good mouse?  I would really like one that (for the most part)  Just plug n plays :D All the talk of editing the xorg.conf scares me silly! 

Does anyone out there use a Logitech G9? Im worried that I will buy another mouse and have the same problem :S Because I really rely on the side buttons.... I neeeeed them!.

Any help/advice much appreciated :)

---

### Post by Dark Hornet on 2007-11-21
personally, I don't like the wireless mice, as I seem to always have issues with the batteries dying, or it simply losing connection at the wrong time.  Right now, I am using a normal "corded" mouse.....have you checked...do they have a corded version of the mouse you are using?

---

### Post by Envy0pla on 2007-11-23
Just in case anyone out there is watching with interest :)  

I have found how to have my mouse seen and working all the time.  Haven't quite figured out how to get the buttons working correctly :D  but at least the first problem is solved! :D 

Here's the link to the site that helped me :D [http://sernaonubuntu.wikidot.com/mouse](http://sernaonubuntu.wikidot.com/mouse)

In particular the info about saving the conf file was very helpful :D 

Thank you for your reply Dark Hornet  :)

---

### Post by Sockerdrickan on 2007-11-24
I would get the latest Razer available!! :D

---

### Post by dbreton on 2007-12-01
Razer does not support linux.  If you do go with a razer I believe there are open source copperhead drivers available.

---

### Post by compiledkernel on 2007-12-02
been using the Razer Diamondback for a good long while. 

Refer here -- [http://www.kw-studios.com/dkblog/?p=9](http://www.kw-studios.com/dkblog/?p=9)

and 

here -- [http://ubuntuforums.org/showthread.php?t=96291](http://ubuntuforums.org/showthread.php?t=96291)

---

### Post by dlpfmVfH on 2008-01-06
I use a G9 laser mouse, in ubuntu, and I must tell you
it works perfectly. 

The only problem I had was to set up all buttons,
but I made a how to for anyone that uses a G9 
see [http://ubuntuforums.org/showthread.php?t=652092](http://ubuntuforums.org/showthread.php?t=652092)

I even talked to the developer of Lomoco, a program to set dpi for logitech mouses in linux, to get the G9 working with this program, in the next version of lomoco the G9 is supported.

But even without lomoco you can set the DPI on the fly with the buttons on the mouse.

---

### Post by Cresho on 2008-01-06
i use a mx518 from logitech.

and to enable the buttons, i do this.

sudo gedit /etc/X11/xorg.conf



Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Resolution" "800" #optional
Option "Buttons" "10"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection


--------------------------------------------------------------------------------
xorg mouse sectionbackup


Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

just remove the bottom (or what it looks like) and att the top part..  I play unreal 2004 with all buttons.

---

### Post by Sadaiyappan on 2008-01-11
I use a Logitech G5.  And it works perfectly -- all buttons including scroll wheel tilting and side buttons were working okay out of the box.

---

### Post by ranklism on 2008-02-05
Razer mouses do work i'm using one right now, just installed ubuntu yesterday best os i've ever used.

---

### Post by Lord Illidan on 2008-02-05
> **dbreton said:**
> Razer does not support linux.  If you do go with a razer I believe there are open source copperhead drivers available.

I am using a copperhead, works great. The side buttons don't work that well, but that's life :(

---

