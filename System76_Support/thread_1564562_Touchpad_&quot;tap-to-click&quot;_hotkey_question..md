---
title: "Touchpad &quot;tap-to-click&quot; hotkey question..."
date: 2010-08-30
forum: System76 Support
---

### Post by isaacullah on 2010-08-30
Hi all,

    I've had my PanP7 for a few months now, and I LOVE it. There is one  thing that I'd like to figure out, however, about the touchpad. It's not  a problem, but rather more of an "annoyance" that I'd like to fix. I  use the touchpad a lot, and I think it's a really great touchpad. I also  really like the ability to just tap on it to click (tap-to-click). It's  a real time saver when surfing the web or when using a complicated GUI  with lot's of buttons! 

     But that feature starts to be an annoyance as soon as you start to type  something (especially in a word processor or in a web form). You  accidentally hit the touch pad with the side of your hand, and your  cursor is put somewhere else! It can get a little frustrating. I know  that there is a hot key that completely disables the touch pad, but I  find that kind of useless because I still need to use the cursor and to  click stuff. What I was wondering is that if anyone knew of a way to  make the "disable touchpad" hotkey (Function F1) turn into a "disable  tap-to-click" hotkey? I know you can disable tap-to-click in the mouse  preferences dialog under the touchpad tab (uncheck the box that says  "Enable mouse clicks with the touchpad"). That tells me that I ought to  somehow be able to turn that into a keyboard shortcut, and therefore I  ought to be able to reprogram the hotkey to do that new function. 

        It  would be a real time saver (going to the mouse preferences dialog takes  time), and would let me keep most of the touchpad functional for when I  am doing word processing, and then quickly turn on tap-to-click when I  am web-surfing or doing something else. 

Any suggestions would be greatly  appreciated!

---

### Post by zpletan on 2010-08-30
Try this:

Paste the following into a script:
```
#!/bin/bash
KEY=/desktop/gnome/peripherals/touchpad/tap_to_click
ON=$(gconftool --get /desktop/gnome/peripherals/touchpad/tap_to_click)

if [ "$ON" = "true" ] ; then
	FLAG=false
else
	FLAG=true
fi

gconftool --set $KEY $FLAG --type bool
```

Set the script executable, then click the "Add" button at the bottom of the Keyboard Shortcuts dialog, and make things how you want them.

---

### Post by zpletan on 2010-08-30
You might also have to unset the disable touchpad functionality, but I don't know how to do that since I'm sitting at a desktop with a mouse.  :)

---

### Post by isantop on 2010-09-01
The problem with remapping the key is that it disables the touchpad at the Hardware level. It's sort of hardcoded into the BIOS to provide this sort of functionality, so Ubuntu will not recognize it as a keypress. 

There is an option in the Mouse Settings dialog (System >Preferences > Mouse) that allows you to disable the touchpad only while typing. I've tested it out on my PanP7 running Lucid, and it seems to work pretty well. There's also a utility called touchfreeze, which may work for you, though I haven't tested it in Lucid. It does about the same thing as that option in the Mouse Settings.

---

### Post by yagolf on 2011-09-05
> **zpletan said:**
> Try this:

Paste the following into a script:
```
#!/bin/bash
KEY=/desktop/gnome/peripherals/touchpad/tap_to_click
ON=$(gconftool --get /desktop/gnome/peripherals/touchpad/tap_to_click)

if [ "$ON" = "true" ] ; then
	FLAG=false
else
	FLAG=true
fi

gconftool --set $KEY $FLAG --type bool
```

Set the script executable, then click the "Add" button at the bottom of the Keyboard Shortcuts dialog, and make things how you want them.

Brilliant! It works like a charm in Mint 11 (I'm guessing it also works on Ubuntu 11.04 with gnome). I have been looking for a nice and easy way to do this and I somehow have been missing this post for a long time. I suppose I wasn't asking the right questions...

Thanks a lot zpletan!
:guitar:

---

### Post by yagolf on 2012-03-08
Hi there again!

I have now moved on to using gnome 3 (thank *** for gnome-extensions) and the simplest and best script ever (see above) doesn't work any more.
 
Is there anything I can change to make it work? As far as I can see (though I'm not that knowledgable), it should work, but it doesn't!
:(
Any ideas? pretty please?

---

### Post by zpletan on 2012-03-08
The difference is that in GNOME 3, GNOME basically switched from GConf to GSettings. The below updated script should do it, then (tested on Oneiric).

```
#!/bin/bash
KEY="org.gnome.settings-daemon.peripherals.touchpad tap-to-click"
ON=$(gsettings get $KEY)

if [ "$ON" = "true" ] ; then
        FLAG=false
else
        FLAG=true
fi

gsettings set $KEY $FLAG
```

---

### Post by tom king on 2012-03-14
Great free tool in Software Center > dconf Editor < that allows  you to fix/change anything (almost) in 11.10. Using the check boxes I  turned my touch pad off only when typing or you can disable it  completely.  Great tool for not techie buntoos. ):P

---

### Post by fallenstar on 2012-03-19
help!

I need to disable my tap-to-click in kubuntu. I have installed dconf but it doesn't run in gui mode. I can get the editor up though. is it just for gnome?

I don't care about the hotkey, I just need it to stop tapclicking permanently!

---

### Post by isantop on 2012-03-22
If you open up the System Settings application, you can go to the "Mouse and Touchpad" section, then open the Touchpad tab and disable clicking with the touchpad (The physical buttons will work fine).

---

