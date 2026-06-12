---
title: "Power Indicator Problem"
date: 2012-02-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by PilotPaul on 2012-02-16
Anyone else having problems with the power indicator?  Mine seems to have stopped reporting battery time left - or at least the time it suggests is not being updated.

acpi & acpitool give a reasonable estimate, and upower is reporting events correctly, so I suspect it is something to do with the indicator applet itself.

I'll investigate further and file a bug if necessary.

---

### Post by badhorse on 2012-02-16
Same problem here, so you're not alone!

Acer Aspire one d255e

---

### Post by bmbaker on 2012-02-16
you are not alone :-)

---

### Post by macstevejb on 2012-02-16
I have a similar problem except that after some recent updates, I now have TWO battery indicators appearing in the top panel!?

:-?

---

### Post by jbicha on 2012-02-16
Have you tried rebooting? gnome-settings-daemon was just updated this week to 3.3.5.

---

### Post by macstevejb on 2012-02-16
oops 2nd battery indicator solved...had it on my whitelisted apps

:oops:

---

### Post by shuttleworthwannabe on 2012-02-16
Yup--same here in Unity only--Gnome shell works fine,

---

### Post by PilotPaul on 2012-02-16
Not a reboot issue (given that this is a development version I always reboot after any updates).  

MeterScreenlet battery indicator seems to show correct battery levels, so it looks to me like an indicator problem.  The indicator is not updating either with a change in charge staus (i.e. unplugging adapter) or with battery discharge.

"upower -m" logs status changes correctly.

This was working correctly up until a couple of days ago (I think!) - something obviously borked it.....

Update: Bug filed in Launchpad as bug [#933646]("https://bugs.launchpad.net/indicator-power/+bug/933646")

---

### Post by shuttleworthwannabe on 2012-02-16
I take it back-- Gnome Shell also does not update the applet--stuck on 84% on mine. Thanks for filing the bug.

---

### Post by PilotPaul on 2012-02-16
Confirmed as duplicate of bug [#933466]("https://bugs.launchpad.net/bugs/933466")

---

### Post by PilotPaul on 2012-02-18
Fix released seems to restore the indicator behaviour but now it doesn't seem to detect me closing the lid (I usually set it to suspend on lid closure when on battery).

Anyone else confirm this?

---

### Post by shuttleworthwannabe on 2012-02-18
Yup--mine hangs from resume from lid closure. Had to do hard powerdown.

---

### Post by PilotPaul on 2012-02-18
Just to confirm my suspend/resume works fine if manually initiated - it is just the lid closure that doesn't seem to work (i.e. it doesn't even try to suspend).

---

