---
title: "Tray icon support in Java broken when using compiz"
date: 2008-05-10
forum: Ubuntu Brainstorm
---

### Post by sistoviejo on 2008-05-10
System tray icon doesn't work in java apps when using compiz. 
Tray icon support was added since java 6 and is a nice thing to add to applications.
It would be nice to have this fixed.
A workaround is to use metacity and disable compiz.

---

### Post by smartboyathome on 2008-05-10
Report this on launchpad, that is all you can do unless you have acess to Java's source or can write a workaround plugin for Compiz.

---

### Post by sistoviejo on 2008-05-11
> **smartboyathome said:**
> Report this on launchpad, that is all you can do unless you have acess to Java's source or can write a workaround plugin for Compiz.

No need for that. Java 1.6 beta 10 fixes the problem. :)
I have just tried it and found this out.

---

### Post by kaaredump on 2008-06-05
> **sistoviejo said:**
> No need for that. Java 1.6 beta 10 fixes the problem. :)
I have just tried it and found this out.

What?? I just installed Java 1.6 beta 10, but it did not do the trick for me!
SystemTray.isSupported() still returns false, and I get no tray icon!

Did you actually get tray icons working under Compiz, or did I totally missunderstand you?

---

### Post by akpuf on 2008-07-05
% java -version

java version "1.6.0_10-beta"
Java(TM) SE Runtime Environment (build 1.6.0_10-beta-b25)
Java HotSpot(TM) Server VM (build 11.0-b12, mixed mode)

Works for me.  The Icon appears in the system tray correctly.  It didn't work with 1.6.0_06.

---

### Post by Seine on 2008-08-20
For me, running Hardy Heron with Compiz on:
[LIST]
[*]Java(TM) SE Runtime Environment (build 1.6.0_06-b02) - **[COLOR="Red"]No TrayIcon (UnsupportedOperationException)[/COLOR]**
[*]Java(TM) SE Runtime Environment (build 1.6.0_10-rc-b28 ) - **[COLOR="Green"]TrayIcon works OK[/COLOR]**
[/LIST]

---

### Post by gmclachl on 2008-08-25
Yeah it was a bit annoying, nice to see it has been fixed. I wrote a small library with java bindings to do this Gnome, I guess I can throw it away now ;-(

George

---

