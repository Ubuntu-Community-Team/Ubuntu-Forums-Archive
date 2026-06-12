---
title: "Unity dash change in mouse behaviour  when launching apps?"
date: 2013-06-15
forum: Ubuntu Development Version
---

### Post by nuttzo31 on 2013-06-15
Is canonical changing the behaviour of the unity dash in 13.10? As it is now you have to double click apps in the dash to open them and a single click opens the preview windows but you can open an app with a single click from the launcher.

Surely this is a bug and not a new feature, perhaps someone else knows?

---

### Post by Chanath on 2013-06-15
I would like to know how to disable the double-click in the unity dash. I really don't need to read about the application. Does someone know?

---

### Post by mc4man on 2013-06-15
It's currently working as coded, whether they will change for desktop installs no clue.

Seen similarly in alt+f2, clicking on a command opens a non -functional preview.  Only mentioning because that is a bug & was fixed (not yet released),  by giving  the command box a 'prefix "x-unity-no-preview'. So it may require another special case for desktop installs, seems unlikely but possible

Not that I expect much - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1191452](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1191452)

---

### Post by scradock on 2013-06-15
Confirmed the bug and added tag: amd64

---

### Post by nuttzo31 on 2013-06-16
> **Chanath said:**
> I would like to know how to disable the double-click in the unity dash. I really don't need to read about the application. Does someone know?

To disable it run dconf-editor from the terminal and navigate to com/canonical/unity and uncheck double-click-activate.

---

### Post by mc4man on 2013-06-16
> **nuttzo31 said:**
> To disable it run dconf-editor from the terminal and navigate to com/canonical/unity and uncheck double-click-activate.
That was easy.. will invalidate bug

---

### Post by Chanath on 2013-06-16
> **nuttzo31 said:**
> To disable it run dconf-editor from the terminal and navigate to com/canonical/unity and uncheck double-click-activate.

Thanks!
Did the job & life became easier.:)

---

### Post by nj1n on 2013-06-17
Please if you don't like the new unity's behavior, just mark as affecting you without add comments, thanks.

[URL="https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189088"]https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1189088


[/URL]

---

### Post by EgoGratis on 2013-06-17
Double click is exactly one click too many...

---

### Post by scradock on 2013-06-17
Hmmm - the change in dconf-editor doesn't seem to be effective for me. The behavior of the dash stays the same (lmb OR rmb --> preview, double lmb --> launch).

If I restart, the setting in dconf reverts to the default, as far as I can see.

PS even logout/login resets to the default, with the "double-click" option checked!

---

### Post by PJs Ronin on 2013-06-18
This is one of those things that really get's my dander up with Ubuntu.   The OS goes along happily, bringing in new functionality, and imo becoming a viable alternative to Windows/Apple, and then it does crazy stuff like this.   If developers really want to alienate customers they should do 2 things.

1.   Change the behavior of something very simple.
2.   Bury the reversal of that change deep in a newbe danger zone.

Is it important for a DE to act the same as an ME... not in my opinion.

/rant

---

### Post by mc4man on 2013-06-18
From their current perspective & focus for 13.10 it makes perfect sense to have the default as is now. When they eventually get around more towards the desktop install then it could be reconsidered, either changing the default action on a desktop install & or providing a more visible means to set. 
(either wouldn't be that hard to do.
Fortunately  there is a means for desktop users to change if desired (or at least atm there is...), likely most desktop users will prefer the old default.

---

### Post by mc4man on 2013-07-11
It's been decided & a fix committed to have applications launch from the left click, all else will for now remain the same.
Desktop users still have the option to globally change for all in dconf though it should not be assumed that option will always be there.

---

### Post by rgara on 2013-08-19
I don't have this option?

When I navigate to com.canonical.unity, I see:

form-factor
home-expanded
minimize-count
minimize-fast-duration
minimize-slow-duration
minimize-speed-threshold

But no double-click-activate

I also see sub headings for

dash
devices
launcher
lenses
webapps


None of those categories contain double-click-activate either. Also tried to use "find". Came up empty.

---

### Post by Mateusz Stachowski on 2013-08-19
You don't have that option because the mouse behaviour has already been changed. One left click on program icon opens it up and the preview is under right click. Other content displayed in the dash will display the preview no matter if you left click or right click.

---

### Post by rgara on 2013-08-19
Yeah, I see now. Thanks for the note and sorry for the forum noise.

---

### Post by mc4man on 2013-08-19
> **Mateusz Stachowski said:**
> You don't have that option because the mouse behaviour has already been changed. One left click on program icon opens it up and the preview is under right click. Other content displayed in the dash will display the preview no matter if you left click or right click.
No - the option to globally change all lens/scopes  to l. click open, r. click preview is still there & available.
screen from todays image

---

