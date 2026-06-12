---
title: "Meerkat or other desktops suspending"
date: 2010-03-17
forum: System76 Support
---

### Post by riseringseeker on 2010-03-17
Curious if other desktop users and Meerkat users specifically are using suspend, and/or if they are having any problems doing so.

Tom has told me that System76 does not specifically test for suspend capability on desktops, just laptops, so I need to throw this to the users here.

A friend, on my recommendation, got a new Meerkat Ion, and at first it would suspend with a Ctrl-Alt-Del, and come back from suspend using the anykey without asking for a password.  My friend is a new linux/ubuntu user and he now says it won't suspend, or come back from suspend without asking for a password.  

I'm having trouble figuring out just what he is reporting, and I won't be able to be at his keyboard for a week or more.  The suspend from the menu (top right) would suspend, but require a password to log back on, hitting Ctrl-Alt-Del would bring up a similar menu, and not require a password last I was there, but now he says it's not working at all.

Anyone out there using suspend on a Meerkat and able to wake it up without using a password/login?

---

### Post by thomasaaron on 2010-03-17
You could try running...

gconf-editor

...and going to Apps > gnome-power-manager > lock and making sure the suspend checkbox is NOT selected. See screenshot (it's selected by default there).

---

### Post by riseringseeker on 2010-03-19
> **thomasaaron said:**
> You could try running...

gconf-editor

...and going to Apps > gnome-power-manager > lock and making sure the suspend checkbox is NOT selected. See screenshot (it's selected by default there).

I sent him the above instructions as well as a link to this thread.  I wanted to get that done this morning, as I only have a few hours of internet left, then won't be able to get on-line until I hit Hong Kong day after tomorrow.

Looking at the setup on the Darter, the only thing I have checkmarked there is gnome_keyring_suspend, and it's working just as he would want it to.

I also decided to go ahead and add gconf-editor to the preferences menu on my machine while I was at it.

---

