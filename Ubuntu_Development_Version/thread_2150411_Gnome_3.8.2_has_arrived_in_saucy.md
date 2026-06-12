---
title: "Gnome 3.8.2 has arrived in saucy"
date: 2013-06-01
forum: Ubuntu Development Version
---

### Post by Harry33 on 2013-06-01
The latest updates to saucy includes the missing parts (gnome-shell) of gnome 3.8.2.
Now also the new clutter-1.0 (1.14.4-1) can be upgraded.

New gdm (3.8.1.1) is soon in too.
There is, however, one issue:
dconf-tools was split into dconf-cli and dconf-editor.
But gdm 3.8.1.1 still depends on the transitional dconf-tools.

---

### Post by dino99 on 2013-06-01
now also waiting for nautilus & terminal upgrades

---

### Post by Dolsilwa on 2013-06-01
Are there any significant visual improvements?

---

### Post by dmiranda on 2013-06-01
Yes, see the release notes:

Highlights for GNOME 3.8 include:

[LIST]
[*]A redesigned application launching view, which makes finding applications easier than ever.
[*]Enhanced search, with an updated search results view and new controls for results.
[*]New privacy settings let you contol who has access to the content on your computer.
[*]A new classic mode for those who prefer a more traditional desktop experience.
[*]Improved animation rendering, resulting in smooth transitions and window resizing.
[*]A new Clocks application, which provides world clocks for different time zones as well as alarms, a stopwatch and timer.
[*]Heavily updated settings, with four new settings panels and major updates in many other places.
[*]Many of updates to GNOME applications, including major improvements to the performance of Web, UI enhancements to Documents and a new Contacts editing mode.
[/LIST]


[https://help.gnome.org/misc/release-notes/3.8/](https://help.gnome.org/misc/release-notes/3.8/)

---

### Post by craig10x on 2013-06-01
Is this the first time gnome 3.8 had been added to ubuntu?  I was curious because i read that the bug with the touchpad setting where it does not retain any change in the pointer speed setting you make after you close the window, was fixed in Gnome 3.8 which ubuntu 13.04 doesn't have (uses the previous version)...
Maybe someone could check it for me and let me know if it is fixed now with the gnome 3.8 update...

---

### Post by sgage on 2013-06-01
I just did a fresh install of Ubuntu Gnome from today's daily. The whole thing went completely smoothly, and I was delighted to see that GS 3.8.2 was the version. I think I'm gonna cruise a while with no PPA's or anything - this seems really smooth and stable. For now...

---

### Post by cincinnatus13 on 2013-06-06
Question- I upgraded to 3.8 via the Gnome PPA but am running Ringtail. I do not have clocks nor the privacy settings (though I can verify I'm on 3.8.2 and have the other stuff- ie. frequent/all apps, right click desktop, etc.)
Am I missing something or shouldn't I have the above mentioned stuff as well?

---

### Post by Harry33 on 2013-06-07
> **cincinnatus13 said:**
> Question- I upgraded to 3.8 via the Gnome PPA but am running Ringtail.
...

So you are running Raring Ringtail.
And this is a Ubuntu+1 (Saucy Salamander ATM) forum.

---

### Post by narya on 2013-06-07
> **cincinnatus13 said:**
> Question- I upgraded to 3.8 via the Gnome PPA but am running Ringtail. I do not have clocks nor the privacy settings (though I can verify I'm on 3.8.2 and have the other stuff- ie. frequent/all apps, right click desktop, etc.)
Am I missing something or shouldn't I have the above mentioned stuff as well?

Add the staging ppa too. Then you will have privacy settings. For clocks , weather and note taking apps you can install it with synaptic.

---

### Post by cincinnatus13 on 2013-06-07
^^Ahh...didn't know I needed staging as well. Thanks.

And yes, I understand that this is the saucy (or +1) forum but since they were both 3.8.2, I figured they would be the same.

---

