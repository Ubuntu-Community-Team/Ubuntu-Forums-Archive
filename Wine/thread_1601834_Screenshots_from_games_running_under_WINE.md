---
title: "Screenshots from games running under WINE"
date: 2010-10-20
forum: Wine
---

### Post by bobwyajnr on 2010-10-20
Hi

I posted on the WINE forums - but I thought I would post here as well (since I am running Lucid x64)!!

I finally got Steam : World In Conflict running nicely (including multiplayer) under WINE 1.3.5 after a week or two of failure... I thought I would celebrate by submitting a screen-shot to the WINE AppDB (as well as an AppDB report).

Anyway the problem I am having is that I get large blocky colour banding in my screenshots that is somewhat off-putting (i.e. not a good advert for running games under WINE). I've got Compiz turned off (always for any kind of gaming) and V-Sync enabled in WIC. :confused:

I even tried suspending the WIC.exe process (in a TTYx console window) to try and freeze the frame. Not surprisingly I just got a black screen (in GDM) - till I went back and re-enabled the WIC.exe process!! :mad:

BTW I am just using the standard Ubuntu PRINT-SCREEN function. I tried installing FRAPS (under WINE) but it doesn't do much (it does install and run OK). Presumably it's not able to hook into Ubuntu to enable global shortcut key bindings.


Any thoughts on how to freeze a (WINE game) frame to get a clean screenshot? Or a better screenshot utility? OK I know it's a pointless exercise but hey... :popcorn:

Thanks
Bob

---

### Post by Stunts on 2010-10-20
Many games have an in-game system for taking screenshots. Can this be the case with WiC too?

---

### Post by alexandari on 2010-10-20
[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

this might help you

---

### Post by tqft on 2010-10-20
alt-prtscreen appears to be broken (or fixed depending on your point of view) in 10.10 (Maverick )
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792)



You could try using the system monitor to sleep/pause the wine process

---

### Post by bobwyajnr on 2010-10-20
> **tqft said:**
> alt-prtscreen appears to be broken (or fixed depending on your point of view) in 10.10 (Maverick )
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/642792)

You could try using the system monitor to sleep/pause the wine process

Uhhm not sure what your reference is to Maverick is about... I am running the game fullscreen and just using PRINTSCREEN (not ALT-PRINTSCREEN). I have no intention of using Maverick anyway (not after the grief I had with Intrepid)...

I can't really access the system monitor while the game is running. That's why I tried suspending the wic.exe process in a TTY console (ALT+CTRL+F1). But that stops it frame serving - so the screen is blank when I transfer back to the Gnome session (ALT+CTRL+F7).

Can I apply the 'kill -STOP' flag to a different WINE or native process that would freeze the X-Server (non-destructively!!)?

This would be really useful for me to submit screenshots of graphical glitches - from Windows games running under WINE. Otherwise the 'added' colour bars, all over the PNG image, sort of get in the way... ](*,)

Bob

---

### Post by Stunts on 2010-10-22
> **alexandari said:**
> [http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

this might help you

This is an excellent link!

@OP:
Do none of the methods described in that link work??

---

### Post by bobwyajnr on 2010-10-22
> **alexandari said:**
> [http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux](http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux)

this might help you

Hey thanks **alexandari**,

Sorry I did kind of overlook your post...

I came up with this shell script using that link (using the ImageMagick application):
```
#!/bin/bash
sleep 360
for (( c=1; c<=1000; c++ ))
do
    import -window root -resize 800 "/home/robert/Pictures/screenshot($c).png"
    sleep 30
done

```

Now I get lots of screenshots of World in Conflict (at the right resolution/file size) and about 95% of them have no visual corruption!! Sweet :popcorn:

Off to AppDB to submit them now...

Thanks a million,
Bob

---

