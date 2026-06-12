---
title: "Artful Freezes."
date: 2017-09-09
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2017-09-09
Tried Arful daily today.  When running live system freezes when trying to open settings.  First install with manual login freezes after entering password, gray screen only and no mouse.  Second install with auto login, system freezes when opening settings, no mouse. i am thinking the problem might be with kernel 4.12.  Any thoughts on this.

Henry

---

### Post by BenginM on 2017-09-11
My system hasn't had a freeze in Artful , and the kernel base currently in use is 4.12.0-11-generic .

---

### Post by Hewjr100 on 2017-09-11
No luck here. Have tried several times and cannot get Artful to boot.

---

### Post by BenginM on 2017-09-11
Which graphic card the system bootin' with ?

---

### Post by Hewjr100 on 2017-09-11
Intel 620.

---

### Post by BenginM on 2017-09-11
That's odd! i presumed the nvidia card. Intel's GPUs usually don't have issues.

---

### Post by BenginM on 2017-09-11
I thought you could try to load the beta1, or an alpha iso image instead of the daily build, but didn't find any as of yet. I even asked in the devs IRC channel.

---

### Post by cariboo on 2017-09-11
> **BenginM said:**
> I thought you could try to load the beta1, or an alpha iso image instead of the daily build, but didn't find any as of yet. I even asked in the devs IRC channel.

Ubuntu doesn't do alpha or beta releases, it is only the flavours that do.

---

### Post by flocculant on 2017-09-11
> **cariboo said:**
> Ubuntu doesn't do alpha or beta releases, it is only the flavours that do.

They do the final beta though.

No that helps at all ;)

---

### Post by deadflowr on 2017-09-11
Have you tried switching sessions?
the default, I guess, should be wayland.
There should also be an Xorg session you can choose at the login screen (toggle the gear icon that appears when you select your username, and before you input the login password.)
(since this is an autologin, you will need to logout and select the session; though I'm not sure about how well gdm session handle autologin and logouts.
(As to whether the logout holds at the login screen or simply relogins quickly, if that makes sense)

---

### Post by grappler on 2017-10-11
Artful running on a Lenovo Thinkpad X1 Yoga (with a touch screen) stops working after suspend - not completely but unusably.  Some but not all mouse actions still work - including motion -  but keyboard stops working. Have to go to another console and issue the command "gnome-session-quit". This results in me losing unsaved work in, say, gnumeric. This seems to happen no matter whether I use Xorg or Wayland. I'm wondering whether this might be caused by some of the extensions to gnome I have installed.  Kernel is  4.13.0-12-lowlatency. Maybe I'll switch back to regular kernel.

---

