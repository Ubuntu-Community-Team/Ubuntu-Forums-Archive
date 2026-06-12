---
title: "ubuntu srever 8.04.1 vga screen res issues"
date: 2008-07-29
forum: Server Platforms
---

### Post by matthewaveryusa on 2008-07-29
Off the bat for my first post: I've been using ubuntu for 3 days, never touched a linux system before in my life and I have a mysql already up and running, so thanks for the great support.

so I tried to change my terminal screen resolution using the vga=xxx in the grub menu.lst

my screen is 1280*1024 native (dell). so I input 794, update-grub,reboot => blank screen with a message from the dell screen => does not support this resolution.

The system is however running perfectly since I rebooted it blind-eyed. 

I repeat all the steps (in "ubuntu safemode") but with vga=791 which is a notch lower than my native screen resolution. Works fine :confused:. any tips?

---

### Post by theolster on 2008-07-29
I had problems configuring this too.  Some time ago ubuntu changed the way that grub handles screen sizes.  [The tutorial I found was here.]("http://crunchbang.org/archives/2007/10/10/changing-bootup-and-console-screen-resolutions/")

So for you the line would probably read something like this:```
... vga=0x31A
```

---

### Post by matthewaveryusa on 2008-07-29
Doesn't work, I get a blank screen again... I'm running my server on a dell PE 2650...  any chances this is a video driver issue?

---

### Post by theolster on 2008-07-29
Yup, could be but unlikely.  Have you tried other settings in the tutorial I linked to?  changing the colour depth could also fix it.

I know this sounds silly, but the monitor really can take the resolution you want?  What monitor model is it?

---

### Post by theolster on 2008-07-29
Sorry bad grammar - Can the monitor take you want? 1280x1024?

---

