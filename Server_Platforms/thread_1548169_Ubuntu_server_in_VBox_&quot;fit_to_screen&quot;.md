---
title: "Ubuntu server in VBox &quot;fit to screen&quot;"
date: 2010-08-07
forum: Server Platforms
---

### Post by OxentroT on 2010-08-07
I just installed Ubuntu Server into VBox and I am wondering how I can be able to fit it to my monitor full screen. Guest additions seems to be un responsive at the moment at least.

---

### Post by Bachstelze on 2010-08-07
You'll need to adjust the framebuffer resolution, but seriously, why would you want to do that?

---

### Post by zephyrblade on 2010-08-07
If you're not fussy, you could just install xorg ? It'll pick up fullscreen then.

---

### Post by OxentroT on 2010-08-08
Ah! Thank You!

---

### Post by VcDeveloper on 2010-10-28
> **OxentroT said:**
> Ah! Thank You!

I would like to do the same thing.  Would you mind sharing what you did?  I setting a LAMP server in 10.10.

THanks!

---

### Post by david.garceau on 2010-10-28
VcDeveloper,
In my experiences, with virtualbox, once you install the guest additions, restart the guest, and it should work for you...

---

### Post by VcDeveloper on 2010-10-29
> **david.garceau said:**
> VcDeveloper,
In my experiences, with virtualbox, once you install the guest additions, restart the guest, and it should work for you...

This will work in console mode also?  I'm not running the Desktop Server version.

---

### Post by carlitos.10040 on 2010-10-29
If you have networking enabled just ssh into it.
No need to install anything except for ssh server.

---

### Post by VcDeveloper on 2010-10-29
> **carlitos.10040 said:**
> If you have networking enabled just ssh into it.
No need to install anything except for ssh server.

I didn't think of that.... good idea!  Also I figured it out [here with these posts]("http://ubuntuforums.org/showthread.php?p=10044027&posted=1#post10044027"), but just need to know one thing....

---

