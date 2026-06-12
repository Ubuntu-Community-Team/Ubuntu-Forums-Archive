---
title: "Which side are the window icons on?"
date: 2010-03-05
forum: The Cafe
---

### Post by Madspyman on 2010-03-05
Seems that no one can decide whether the window buttons should be on the right or the left in Lucid, why not let the user decide.

I know it's already possible to move them by changing the metacity settings in gconf-editor, but thats not something a new to Ubuntu user would be thinking of.

How about being able to back click on the window and choose from a drop-down menu what side to have the icons on.

Also during installation you could have the option of "legacy settings" (right placement) or "light settings" (left placement).

I don't think there's another distro that offers this as a standard option, other than in gconf-editor. Might be kinda cool.

---

### Post by Madspyman on 2010-03-05
Sorry I suppose this wasn't aptly titled. Perhaps it's in the wrong place?

---

### Post by Post Monkeh on 2010-03-05
i'd say it's just that the issue has been debated to death over the past couple of days

---

### Post by Austin25 on 2010-03-05
Left side is the way it comes in Windows and in Karmic, so if you are looking for it to look natural, Left side would be the way to go. IMHO though, it does not really matter what side it is on. If you want Lucid to look different, then put it on the right.

---

### Post by Madspyman on 2010-03-05
> If you want Lucid to look different, then put it on the right.

That's kinda what I was suggesting.

I don't feel, I'm getting any clear answers, especially when during testing as they keep changing from one side to the other.

Figured I'd offer up a solution that might benefit both sides of this argument.

---

### Post by samh785 on 2010-03-05
> **austin25 said:**
> right side is the way it comes in windows and in karmic, so if you are looking for it to look natural, right side would be the way to go. Imho though, it does not really matter what side it is on. If you want lucid to look different, then put it on the left.
ftfy

---

### Post by Jesus_Valdez on 2010-03-05
Is really easy change the position of the buttons on the window layout using gconf-editor on  /apps/metacity/general/button_layout

---

### Post by tjwoosta on 2010-03-05
> **Jesus_Valdez said:**
> Is really easy change the position of the buttons on the window layout using gconf-editor on  /apps/metacity/general/button_layout

...

[quote=Madspyman]I know it's already possible to move them by changing the metacity settings in gconf-editor, but thats not something a new to Ubuntu user would be thinking of.[/quote]

---

### Post by Jags_FL on 2010-03-05
> **Jesus_Valdez said:**
> Is really easy change the position of the buttons on the window layout using gconf-editor on  /apps/metacity/general/button_layout

thanks a million... 

if anyone else is looking for the same in nightly Lucid builds, by changing from "maximize,minimize,close:" to

**menu:minimize,maximize,close**

window button layout will be the way it was before.

---

### Post by Madspyman on 2010-03-06
> Is really easy change the position of the buttons on the window layout using gconf-editor on /apps/metacity/general/button_layout

I believe I mentioned that in the first post, I suppose I should have named the thread something different, I was expressing an idea to help new users change things w/o having to google the answer.

---

