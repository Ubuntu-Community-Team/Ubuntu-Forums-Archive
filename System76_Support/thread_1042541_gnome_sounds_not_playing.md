---
title: "gnome sounds not playing"
date: 2009-01-17
forum: System76 Support
---

### Post by eyecreate on 2009-01-17
I just noticed this problem because I was trying to change the sounds in gnome to custom sounds. It seems that only the login/logout sounds actually play, whereas, no matter what sounds are already there or I replace with custom sounds of any type, they will not play in gnome. ex. I tried to change the empty the trash sound and no matter how many times I made a empty file, deleted it, and emptied the trash, there would be no sound. What could cause this?

---

### Post by thomasaaron on 2009-01-17
Are you adding your own custom sound files? If so, make sure they are the same format as the originals... I believe they are .ogg

Also, you probably have to reboot after making changes.

Let me know if I'm misunderstanding.

---

### Post by eyecreate on 2009-01-17
I will try rebooting on custom sounds, but I don't know if that is it. It doesn't seem to just be custom sounds, but also default sounds that came installed. I never have heard the ubuntu warning sound on my computer and didn't know there was one till I looked in the sound menu. It seems to just not be playing them.

---

### Post by thomasaaron on 2009-01-17
I get a single drum beat for the Warning sound.
I don't get a Battery warning sound though.

I'm testing in System > Prefs > Sound > Sounds.

Maybe you just need to assign them. To find all (or most) of your system's sounds run...

locate *.wav

Most of them are in /usr/share/sounds/

---

### Post by makro on 2009-01-18
I can confirm sounds for buttons click and alert dialogs don't work in intrepid. Any helps? (I've enabled them in System/Sounds)

---

### Post by thomasaaron on 2009-01-18
Hi, Macro.

Look at the thread just above yours. Try to assign custom sounds to whatever you want.

I'll tinker with it when I get back in the office tomorrow.

---

### Post by eyecreate on 2009-01-18
it's not that it can't find the sounds, as when I click the play preview button, I hear the sound that should play, but it never plays for real.

---

### Post by thomasaaron on 2009-01-18
Bingo...

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507)

---

### Post by eyecreate on 2009-01-19
i think that fixed it. thanks!

---

