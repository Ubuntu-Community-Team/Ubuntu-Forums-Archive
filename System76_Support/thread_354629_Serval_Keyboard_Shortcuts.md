---
title: "Serval Keyboard Shortcuts"
date: 2007-02-06
forum: System76 Support
---

### Post by steveneddy on 2007-02-06
Anyone know any of the keyboard shortcuts for the Serval Laptop from System76?

I have found the Fn+F1-F12 keys, but I am looking for the one that turns off the touchpad if one exists.

-SE

**EDIT**
Here's what I found for KB shortcuts:

Fn+F1=suspend or maybe hibernate
Fn+F2=unknown at this time - maybe second screen control
Fn+F3=unknown at this time - maybe second screen control
Fn+F4=make screen darker
Fn+F5=make screen brighter
Fn+F6=volume mute
Fn+F7=volume down
Fn+F8=volume up
Fn=F9-F12=unknown at this time

Anyone know of any more? Or how to set up anymore?

---

### Post by crichell on 2007-02-06
There is no key combination for the touchpad, however, you can run:
```

sudo rmmod psmouse
```

Which will turn off the mouse and still allow you to use an external USB mouse.  Run

```
sudo modprobe psmouse
```

To turn it back on.

---

### Post by steveneddy on 2007-02-06
> **crichell said:**
> There is no key combination for the touchpad, however, you can run:
```

sudo rmmod psmouse
```

Which will turn off the mouse and still allow you to use an external USB mouse.  Run

```
sudo modprobe psmouse
```

To turn it back on.

You can also do:

```

sudo -S rmmod psmouse
```

and

```
sudo -S modprobe psmouse
```

.....The -S part makes it so one doesn't have to enter a password.

So - how do I make this into a script so I can run it from a button or a KB shortcut so I don't have to enter lines of code whenever I need to turn it off and not think about it. 

This is a great tip, Carl. Thank you very much. It has saved my sanity from touching the Touchpad and scrolling to the bottom of the document I'm working on.

-SE

The laptop rocks, dude. Thanks again.

---

### Post by sgtron on 2007-02-07
Fn+F3 may look like a way to change monitors, but I've been told the only way to change monitors is to use YANC.

As for the volume controls.  Mine don't seem to work.  Fn+F6 says it's muting, but I can still hear sound.  Although I get an icon on my display that says it's muting.

---

### Post by crichell on 2007-02-07
We ran across the volume control problem before.  The hot keys are adjusting Headphone volume rather than PCM or Front.  There is a fix in this post.

[http://ubuntuforums.org/showthread.php?t=242996&highlight=serval+volume+control](http://ubuntuforums.org/showthread.php?t=242996&highlight=serval+volume+control)

---

