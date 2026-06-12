---
title: "Development idea: GUI frontend for script?"
date: 2007-07-16
forum: Ubuntuzilla
---

### Post by aysiu on 2007-07-16
Recently, I found out about Zenity, which provides GTK dialogs for shell script actions (error messages, file upload selection, progress bars, confirmation dialogs, etc.)

I realize the script is now written in python, but could Zenity make an easy GUI frontend for it? And, if so, would it be worth implementing, and how would that affect KDE users?

---

### Post by vambo on 2007-07-16
Could someone explain the point of this?:confused:

---

### Post by EndPerform on 2007-07-16
> **aysiu said:**
> Recently, I found out about Zenity, which provides GTK dialogs for shell script actions (error messages, file upload selection, progress bars, confirmation dialogs, etc.)

I realize the script is now written in python, but could Zenity make an easy GUI frontend for it? And, if so, would it be worth implementing, and how would that affect KDE users?

Why not use Python's GTK bindings?

---

### Post by aysiu on 2007-07-16
> **EndPerform said:**
> Why not use Python's GTK bindings? Or that. Is that something difficult to implement?

> **vambo said:**
> Could someone explain the point of this?:confused: The point of a GUI? Sometimes people just like point-and-click stuff. They view that as "friendlier."

---

### Post by vambo on 2007-07-16
Maybe, but it seems to be an awfully long way for a short cut ;)

---

### Post by aysiu on 2007-07-16
> **vambo said:**
> Maybe, but it seems to be an awfully long way for a short cut ;)
I'm not sure what you're saying exactly.

---

### Post by EndPerform on 2007-07-16
Well, it might take a little bit to learn the bindings, but in the long run it would work out for the best.  I've seen some pretty awesome apps coded in python :)

---

### Post by MystaMax on 2007-07-18
I'm all for a GUI. It'd be a great addition, and you've got my vote!

---

### Post by the.phantom on 2007-07-19
if it could be done in a gui i think that would be some kind of great !

a lot of folks like Ubuntu, but are in no hurry to learn "the care and feeding of your pet linux"

your script solves a major problem of staying current on mozilla

if you look at it i think Ubuntu is so popular because you don't spend your life in the terminal worrying about trashing the system !
yep even though i am a lightweight i help a few friends with their Ubuntu, and i am even looking at "mint"
as i found it can work xorg without looking at a black screen if you make a bobo !
i think a gui way is the way to go
look at ms, and what happened with win95 where the AVERAGE person could have a computer and do what they want !
i try but the command line is still limited to "copy and paste" for me

just my ideas ;-)
and maybe i would not have to go to a few places each month to "partimage" their systems ;-D

---

### Post by nanotube on 2007-07-23
hm, well, i'll put the gui implementation on my longer-term todo list, seeing as how everyone seems to be in favor. :)

---

### Post by snkiz on 2007-07-24
I really don't know very much about programing but it seems to me it would be easier to make a gui compiler to install/update any source program where it should go within ubuntu no need for anything flashy just simple so it will run under any ubuntu flavor that would end the locked version issue that plagues the package system.

---

### Post by aysiu on 2007-07-24
> **snkiz said:**
> I really don't know very much about programing but it seems to me it would be easier to make a gui compiler to install/update any source program where it should go within ubuntu no need for anything flashy just simple so it will run under any ubuntu flavor that would end the locked version issue that plagues the package system.
That's a separate issue.

This UbuntuZilla script does not compile Firefox, Thunderbird, or Seamonkey. It downloads a precompiled binary and integrates it with the system.

---

