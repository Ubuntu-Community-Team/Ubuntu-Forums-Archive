---
title: "Remote Desktop Viewer Only Grey Screen"
date: 2008-11-30
forum: Server Platforms
---

### Post by CyberPrime on 2008-11-30
Hi, I am not sure if this is exactly the right place for this question but it seems to make sense.
My Remote Desktop Viewer in Ubuntu 8.10 64bit is opening into a fullscreen grey window. The only way I can get out of it is Alt+F4. I don't know why this is happening, but I hasn't always. I forget exactly what I did to cause this but it wasn't any playing around in config files or anything like that. Anybody had this problem before?

---

### Post by boterbram on 2008-12-02
Same error here

Didn't have this at first, only after I got some weird freezes which might have something to do with the program. any ideas?

---

### Post by boterbram on 2008-12-02
Screenshot of the error (upper-left screen obviously)

---

### Post by Kvikvendi on 2008-12-04
I had this too today, the window seems just too large for the screen. I was able to reset it by removing the file ~/.gconf/apps/vinagre/%gconf.xml

So just type ```
mv ~/.gconf/apps/vinagre/%gconf.xml ~/.gconf/apps/vinagre/%gconf.xml_backup
``` in your terminal and you should be good to go ;)

---

### Post by boterbram on 2008-12-05
I "fixed" this too. Just open a vnc server via the terminal using vinagre

so type something like this:

$ vinagre 192.168.1.2

and the screen resolutions are all reset

---

### Post by coodtec on 2008-12-28
> **Kvikvendi said:**
> I had this too today, the window seems just too large for the screen. I was able to reset it by removing the file ~/.gconf/apps/vinagre/%gconf.xml

So just type ```
mv ~/.gconf/apps/vinagre/%gconf.xml ~/.gconf/apps/vinagre/%gconf.xml_backup
``` in your terminal and you should be good to go ;)

But it not works with me. :confused:

---

### Post by coodtec on 2008-12-28
In terminal and type
```
 vinagre 192.168.0.5:1000
``` 

Get error message, but reset, and fix it ;-)

---

