---
title: "New Battery Icon."
date: 2012-09-19
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by donniezazen on 2012-09-19
Hi,

Is this the new battery icon in Ubuntu? It's just too big and doesn't fit with other icons.

[[IMG]http://i.imgur.com/ha5t2.png[/IMG]](http://imgur.com/ha5t2)

What do you guys think?

---

### Post by mcellius on 2012-09-19
I've had that same icon come and go before in previous versions of Ubuntu, but I never understood why.

Today I got it for the first time in QQ.  It happened after the laptop had been unplugged for awhile so it was while it was recharging; now fully charged, the icon has changed back to the smaller and more usual version.

And when I unplug the laptop, the icon again changes to the large version.  I'm guessing it does that so it'll be more noticeable.  This behavior appears to be different than in previous versions.

---

### Post by mc4man on 2012-09-19
The larger icon is likely the symbolic icon, seeing now as the result of the gtk3 upgrade which

> * debian/patches/101_revert_symbolic_icon_search.patch:
    - drop the revert workaround done for precise, the icon theme should 
      be fixed rather in quantal since that's the correct solution,
      the patch also creates issues in gnome-shell (lp: #1001229)

Overall a good thing, finally now getting symbolic icons in nautilus 3.5.92 for all Devices in an Ubuntu session
(though usb & optical media are still getting same icon  has hdd's

---

### Post by qamelian on 2012-09-19
That's the default battery icon for Gnome. There is an update available for the ubuntu-mono package that will restore the icon you are more familiar with.

---

### Post by donniezazen on 2012-09-20
Good to hear that.

---

### Post by serdotlinecho on 2012-09-20
After updating the indicator-power and ubuntu-mono, the battery status now stays in full charge.

---

### Post by commanderwil on 2012-09-20
maybe replace the internal battery?

---

