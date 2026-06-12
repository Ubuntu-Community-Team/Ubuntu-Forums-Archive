---
title: "Volume Buttons in Debian"
date: 2007-12-02
forum: System76 Support
---

### Post by chules1989 on 2007-12-02
Hello,

I'm trying to get Debian as well as Ubuntu working on my System76 Darter Ultra laptop.  Almost everything appears to be working with some tweaking, except for the volume buttons on the side.  These buttons work in Ubuntu, but not in Debian.  Any idea how I can get them working in Debian?

Thanks,
Chris

---

### Post by thomasaaron on 2007-12-03
Are you talking about the little "thumb knob" on the white Darter (DarU1)?
None of our Darters have volume buttons, per se, on the side.

If so, try going to a terminal and running: tail -f /var/log/syslog
Then move the knob and see if you see any kind of message or keycode.

What you will need to do is find a keycode for the button and then program it to adjust the volume. I'm not all that great at it, but I'm sure we can probably figure it out.

---

### Post by chules1989 on 2007-12-03
Yeah, I'm referring to the thumb knob on the DarU1, sorry about the ambiguity.  I tried looking at syslog and a few other logs, but they don't register any keypress (or anything at all) when I move the knob.

Thanks,
Chris

---

### Post by beuno on 2007-12-03
I'm having the same problem here with Debian Lenny (testing).

Actually, none of the keys work  :D

---

### Post by thomasaaron on 2007-12-03
This thread mentions a program that might be your best chance for getting it working. At the very least, it may help you to figure out the keycode.

[http://ubuntuforums.org/showthread.php?t=614644](http://ubuntuforums.org/showthread.php?t=614644)

---

### Post by chules1989 on 2007-12-03
Ok, I installed the xkeycaps program as mentioned in that thread, but no key code shows up when I hit the knob.  I tried a few different keyboards, but none of them seem to work.

---

### Post by thomasaaron on 2007-12-03
Try this:
Go to a terminal and enter: showkey
Then try the knob.

If that doesn't work, I'm fresh out of ideas. We don't do anything special to make that knob work. It's all Ubuntu.

---

### Post by beuno on 2007-12-03
> **thomasaaron said:**
> Try this:
Go to a terminal and enter: showkey
Then try the knob.

If that doesn't work, I'm fresh out of ideas. We don't do anything special to make that knob work. It's all Ubuntu.

Nothing happens when running showkey and pressing the knob.

On the other hand, it does scroll down like crazy, I'm not sure if that's an expected behavior.

---

