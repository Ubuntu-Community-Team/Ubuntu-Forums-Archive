---
title: "Startup script to prevent Xubuntu reloading previous session - safe or not?"
date: 2014-04-18
forum: Ubuntu, Linux and OS Chat
---

### Post by Bill Tetzeli on 2014-04-18
I was hoping that Xubuntu 14.04 would finally solve the problem of previous sessions being loaded at startup, but alas, no.  So I added this script in the Application Autostart tab of Session and Startup in Settings:

rm -r -v ~/.cache/sessions/*


This has proved necessary because doing it in terminal only prevents the previous session from loading for one reboot.  After that the problem starts all over again.  Adding it in Application Autostart seems to fix it permanently, though, by deleting the sessions cache on each login.

My question is, is this safe?  I know slapping code off of just any old website into your system is never a good idea, but this is such an annoying problem (and I don't know why after all these years it hasn't been fixed) that I was desperate.  It seems to work, but I'd sleep better knowing it's benign and not harmful.

TIA

---

### Post by monkeybrain20122 on 2014-04-18
This is ok, it just deletes the contents of ~/.cache/sessions/ on every reboot. But you don't need that, simply lock the sessions folder will do. Right click ~/.cache/sessions delete everything inside and set permission to none will prevent it from re-spawning. I think you can also disable it somewhere in the gui options but it seems to depend on how you logout/shut down.

I agree that it is extremely annoying.

---

### Post by Bill Tetzeli on 2014-04-18
Thank you so much!

I had no idea there were so many ways to cripple, kill and neuter Xubuntu's session cache.  I'll try all of them with my other laptops.  I suddenly feel very powerful and very, very cruel.  Muahahahahahahahahahahahahaaaaaaaa!!!

---

### Post by SurfaceUnits on 2014-04-18
Like if you do like a logoff, there is a check box for this

---

### Post by monkeybrain20122 on 2014-04-18
> **SurfaceUnits said:**
> Like if you do like a logoff, there is a check box for this

I don't have xfce now, but I remember that only works if you shut down in one way but not the other (the button vs the menu, don't remember which one)

---

### Post by Bill Tetzeli on 2014-04-20
Yeah, it's a bit more involved, and then you have to shut down via the logout dialog box each time.  If you shut down using the shutdown or restart buttons directly even once, you're back where you started.  Setting ~/.cache/.sessions privileges to "none" is the way to go - set it and forget it.

---

