---
title: "Can not select Gnome at log in"
date: 2012-09-18
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by victor9098 on 2012-09-18
Hi All,

Just wanted to give GS a try on the PC (have it installed alongside Unity on my other machines) but when I open the list to select it I can not click 'Gnome'. I can select the other two Gnome sessions and Ubuntu, but not the top Gnome option.

Have tried reinstalling the packages but no change, still not able to select. Any thoughts?

---

### Post by sammiev on 2012-09-18
> **victor9098 said:**
> Hi All,

Just wanted to give GS a try on the PC (have it installed alongside Unity on my other machines) but when I open the list to select it I can not click 'Gnome'. I can select the other two Gnome sessions and Ubuntu, but not the top Gnome option.

Have tried reinstalling the packages but no change, still not able to select. Any thoughts?

I was using GS until 1 min a go. I switched out to test if I could go back to it. I could not go back to Gnome. File a bug report and I will add a me to when you post the addie. :)

---

### Post by jfernyhough on 2012-09-18
It's a definite bug. As far as I can tell the click passes through onto the login fields rather than the session selection box.

On a related note, why can't we select the session by using the keyboard?

Workaround: edit ~/.dmrc and change Session= to the one you're after.

---

### Post by victor9098 on 2012-09-18
[Bug #1052453]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1052453") is up on launchpad :guitar:

I filed it against lightdm, but if I am off the mark I am sure it will be soon edited.

---

### Post by mc4man on 2012-09-18
Appears to be an issue with latest unity-greeter package

---

### Post by sammiev on 2012-09-18
> **victor9098 said:**
> [Bug #1052453]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1052453") is up on launchpad :guitar:

I filed it against lightdm, but if I am off the mark I am sure it will be soon edited.

Added my Me To as well. :)

---

### Post by itsjustarumour on 2012-09-27
Getting the same problem when I try to select Cinnamon - can select Cinnamon 2D and all the other Desktop options, just not the regular Cinnamon version.

---

### Post by sammiev on 2012-09-27
> **itsjustarumour said:**
> Getting the same problem when I try to select Cinnamon - can select Cinnamon 2D and all the other Desktop options, just not the regular Cinnamon version.

Look at the bug report and use the Tab and space bar to select.

---

### Post by ELD on 2012-09-27
Looks like they are on it :)

Thought it was a bug with Cinnamon desktop as i had to use tab to get to it heh, the joys of pre-releases eh!

---

