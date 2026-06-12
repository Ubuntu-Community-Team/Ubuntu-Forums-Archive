---
title: "Problems with restart in 12.10"
date: 2012-10-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by northwestern on 2012-10-10
HI
Whenever I update software and then asked to restart the computer (pressing the "Restart" button) my laptop closes as normal, but on restart hangs with a dark screen and a large flashing line in the top left hand corner. I then have to power down the computer by pressing the power button, restart then act as normal. I have tried the five options  provided by the Upubuntu website but unfortunately none of them appear to work.

Any advice please.
Regards.
Northwestern

---

### Post by funicorn on 2012-10-10
```
dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart
```

run this and see what's output

---

### Post by northwestern on 2012-10-10
Thanks for your reply.
Entered your instruction into the terminal and ran, my laptop went into restart mode but still hung at the same place.

Regards
Northwestern

---

### Post by philinux on 2012-10-10
Next time click on the network icon and disable networking the try a restart. Post back of this helps.

---

### Post by northwestern on 2012-10-10
Thanks, turning off the wireless network works a treat, is there any way round having to keep doing this before each restart ?.

Regards
Northwestern

---

### Post by funicorn on 2012-10-10
If you want it to be right, you have to do it right.

This time type this into the terminal
```

dbus-send --system --print-reply --dest="org.freedesktop.ConsoleKit" \
/org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Restart \
2>&1>~/dbus_fail.log

```after you do that, see what the output is in ~/dbus_fail.log

---

### Post by northwestern on 2012-10-11
Did as asked, entered new script in terminal, my laptop tried to restart but still hung in the same place. 

The message in the dbus fail.log read "method return sender=:1.15 -> dest=:1.61 reply_serial=2".

Regards
Northwestern

---

### Post by dino99 on 2012-10-11
> **northwestern said:**
> Did as asked, entered new script in terminal, my laptop tried to restart but still hung in the same place. 

The message in the dbus fail.log read "method return sender=:1.15 -> dest=:1.61 reply_serial=2".

Regards
Northwestern

you should report that output as a addon to what you have explained & done 

ubuntu-bug linux

"restart issues" have already found some solutions but there is at least some others needed to be fixed:
[https://bugs.launchpad.net/ubuntu/natty/+source/libnih/+bug/740390](https://bugs.launchpad.net/ubuntu/natty/+source/libnih/+bug/740390)

---

