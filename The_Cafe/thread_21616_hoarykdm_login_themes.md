---
title: "hoary/kdm login themes?"
date: 2005-03-23
forum: The Cafe
---

### Post by josiah on 2005-03-23
i initially came to ubuntu partially for the easy escape from the world of blue. is there any way to change the kdm screen? the blue `kubuntu' screen is mildly offensive to the world of browns that i've become accostomed to.

---

### Post by jdong on 2005-03-23
kcontrol.

---

### Post by josiah on 2005-03-24
thank you for the effort, but have you tried that, or are you giving me a knee-jerk reply?

perhaps i should have mentioned that in the kde control panel (kcontrol), i can set up the login manager but it does no good. the only option given is that i can change the background, but the new background doesn't show up until *after* i log in (and i'm still stuck with the blue background in the login screen).

---

### Post by Firetech on 2005-04-10
There is an easy way to make KDM follow the rules of kcontrol.
1. Open /etc/kde2/kdm/kdmrc in your favourite text editor (with root privilegies, preferably using sudo)
2. Scroll down until you see the section "[X-*-Greeter]" Scroll down some more, until you see the line "UseTheme=true".
3. Change the line you just found to "UseTheme=false"
4. KDM will now follow the settings you set in kcontrol. The login box will be a window, though.

---

### Post by KiwiNZ on 2005-04-10
[QUOTE=josiah]thank you for the effort, but have you tried that, or are you giving me a knee-jerk reply?

Now now be nice =;

---

