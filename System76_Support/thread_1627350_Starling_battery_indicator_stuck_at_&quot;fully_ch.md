---
title: "Starling battery indicator stuck at &quot;fully charged&quot;"
date: 2010-11-21
forum: System76 Support
---

### Post by macaholic on 2010-11-21
This is a problem I've had since I purchased my Starling. If I charge it up completely, when the battery indicator says "fully charged", and then unplug it, the indicator doesn't change until it hits critically low. The behavior is pretty much identical to what's described in this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572970](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/572970) which is listed  as fixed. Is this fixed in Maverick? If so, is there any way I can fix this without upgrading to 10.10?
Any help/suggestions are greatly appreciated.

---

### Post by teddyprentice on 2011-02-19
I'm having the same issue. Is there another, more recent thread on this issue that I'm missing?

---

### Post by EJJ on 2011-02-19
I get the same thing, though it doesn't happen every single time.

I've noticed it's become more frequent though

---

### Post by tc101 on 2011-02-19
Same here.  I get the same thing, but not always.  

I think there is some pattern to this.  I think if battery is 100% when you turn on the computer the indicator sticks at 100%, but if battery is below 100% then indicator works.  I am not sure of this.

In a pinch you can always open the terminal and enter

 acpi -b

which will give the correct power

---

### Post by ktmhz on 2011-02-23
Just got my new Starling this Monday, and this problem started up right away. Glad this seems to be the only negative issue I am experiencing with my new machine.

---

### Post by Roush 427r on 2011-02-24
Looks like this is a bug that needs fixing on Star4's. I have noticed that when I do a restart, it goes away. Another bug is that sometimes when I am on a media player such as rhythybox or another app, it freezes on my desktop, and I cannot close out of it.

---

### Post by teddyprentice on 2011-02-24
Yes, it doesn't happen all the time with my Star3. My problem seems to be exactly as macaholic originally described it.

The indicator only sticks (perfect word for it, tc101) when my Star3 charges to 100% *while running*. If it fully charges while off, no problem. And even if it fully charges while suspended, no problem. But once the indicator does stick, it seems to stick for good. The only thing that unsticks it, as Roush 427r notes, is a restart.

It's all not that big of a deal, more so just annoying.

---

### Post by isantop on 2011-02-24
Thanks for all of that information. All of that will make it easier to test with this. I'll get to that today.

---

### Post by tanderson on 2011-02-26
This problem has been present for a while. see this thread.

[upower]("http://ubuntuforums.org/showthread.php?t=1576111&highlight=upower")

---

