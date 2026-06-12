---
title: "Which genius decided to disable ctrl+alt+backspace?"
date: 2009-10-16
forum: The Cafe
---

### Post by kraoZ on 2009-10-16
Why has this been disabled? It's one of the most useful features if you're a WINE user and something goes wrong fullscreen!

---

### Post by schauerlich on 2009-10-16
You can enable it by editing /etc/X11/xorg.conf

[http://www.google.com/search?client=safari&rls=en&q=xorg+dontzap&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=safari&rls=en&q=xorg+dontzap&ie=UTF-8&oe=UTF-8)

---

### Post by Sashin on 2009-10-16
alt + printscreen + k seems to work well too somehow.

---

### Post by Mr. Picklesworth on 2009-10-16
> **kraoZ said:**
> Why has this been disabled? It's one of the most useful features if you're a WINE user and something goes wrong fullscreen!

It'll be quicker for you if you switch to a different tty (Ctrl Alt F2 or some such), log in and run "killall wine", for example. Less destructive, too.

The switching tty key combo works at a lower level than Ctrl Alt Backspace, so should work basically anywhere.

---

### Post by kraoZ on 2009-10-16
> **EDavidBurg said:**
> You can enable it by editing /etc/X11/xorg.conf

[http://www.google.com/search?client=safari&rls=en&q=xorg+dontzap&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=safari&rls=en&q=xorg+dontzap&ie=UTF-8&oe=UTF-8)

Thanks.

> **Sashin said:**
> alt + printscreen + k seems to work well too somehow.

Does it do the same thing?

---

### Post by Nerd King on 2009-10-16
> **Mr. Picklesworth said:**
> It'll be quicker for you if you switch to a different tty (Ctrl Alt F2 or some such), log in and run "killall wine", for example. Less destructive, too.

The switching tty key combo works at a lower level than Ctrl Alt Backspace, so should work basically anywhere.
What he said.

---

### Post by Icehuck on 2009-10-16
The X.org developers disabled it and really don't seem to like the functionality.

---

### Post by hobo14 on 2009-10-16
> **Icehuck said:**
> The X.org developers disabled it and really don't seem to like the functionality.

Pity, because a lot of us seem to like it.

---

### Post by Metallion on 2009-10-16
> **kraoZ said:**
> Does it do the same thing?

No, it drops you on a terminal session which is running next to your X session. You could kill wine from there and then type alt+control+F7 to get back to your X.

---

### Post by 3rdalbum on 2009-10-16
> **Icehuck said:**
> The X.org developers disabled it and really don't seem to like the functionality.

They don't have a problem with the functionality. The keyboard combination has just been moved from Control-Alt-Backspace (which some noobs hit thinking it will bring up the Windows task manager) to Alt-PrintScreen-K.

Alt-PrintScreen-K will kill the X server just like Control-Alt-Backspace used to do. And yes, it still works with the XSplash system in Karmic.

---

### Post by t0p on 2009-10-16
Info in [this thread]("http://ubuntuforums.org/showthread.php?t=1178967") on editing xorg.conf.  Or you can install the package **dontzap** and run the command

```
dontzap --disable
```

---

### Post by jeremy on 2009-10-21
Answers here -> [https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

---

