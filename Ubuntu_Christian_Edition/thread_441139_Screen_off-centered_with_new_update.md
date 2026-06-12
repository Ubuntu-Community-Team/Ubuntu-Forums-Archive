---
title: "Screen off-centered with new update"
date: 2007-05-12
forum: Ubuntu Christian Edition
---

### Post by Bodizzle on 2007-05-12
Why is my screen off-centered when I start up with Ubuntu.  It is about a 1/4 of an inch shifted right compared to Windows?  I tried to add a line to xorg.conf as suggested by another forum but that didn't work when I restarted?

---

### Post by NilsE on 2007-05-12
Go into a terminal and run:

sudo dpkg-reconfigure -phigh xserver-xorg

Pick the correct video driver and select the resolutions you like and this will rebuild you video configuration.

---

### Post by Bodizzle on 2007-05-12
That didn't really help.  I only addressed the possible screen resolutions I could use but that isn't the issue.  My resolution is fine but the picture is off centered by 1/4 an inch

---

### Post by heimo on 2007-05-13
> **Bodizzle said:**
> That didn't really help.  I only addressed the possible screen resolutions I could use but that isn't the issue.  My resolution is fine but the picture is off centered by 1/4 an inch

Have you tried using xvidtune to make a new modeline and adding that to your xorg.conf? Some instructions here:
[HOWTO: Solving resolution/refresh rate problems in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by Bodizzle on 2007-05-13
I did do that as well.  That was the first thing I found from another forum but it didn't work.  It told me to  go to xvidtune and adjust until it was centered.  Then press the show button and add that line to xorg.conf by typind Modeline followed by the line that xvidtune gave me.  I saved it but it still is off centered when I boot back up.

---

### Post by heimo on 2007-05-13
Then it's probably not using the new modeline. You could try renaming the modeline (the identifier that's used to refer to it - usually something like "1024x768" - make it unique). Check your xorg log file under /var/log.

---

### Post by Tru on 2007-05-13
You could also just adjust the picture on your monitor.  Every monitor I have ever used has a menu and the ability to move and stretch the picture.  Have you tried this option?

---

### Post by Bodizzle on 2007-05-13
I could do that but I dual boot with Windows which means it would be off centered when I boot to Windows.  It would be really annoying to have to adjust the screen every time I switch my OS so I would like to adjust it permanently.  I will try a couple of other things that I haven't had time to do yet.

---

### Post by Tru on 2007-05-14
Yes, you are right that would be a pain to adjust every time, unless you have an LCD monitor in which case all you would have to do is hit the auto adjust button.  What video card are you using Nvidia or ATI?  I don't really use ATI cards, but with Nvidia's control panel you can usually make adjustments to the screen ie stretching, and moving it.

---

