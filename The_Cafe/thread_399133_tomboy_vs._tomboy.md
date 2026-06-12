---
title: "tomboy vs. tomboy"
date: 2007-04-01
forum: The Cafe
---

### Post by Mateo on 2007-04-01
what's the difference between tomboy the program and tomboy the applet? they both do the exact same things.  they both take up about the same amount of memory.  What's the difference?

---

### Post by ubuntu27 on 2007-04-01
There are two tomboys!!?? 

I didn't know that. :D

---

### Post by ComplexNumber on 2007-04-01
> **Mateo said:**
> what's the difference between tomboy the program and tomboy the applet? they both do the exact same things.  they both take up about the same amount of memory.  What's the difference?
what makes you think there is a program *and* an applet?

---

### Post by Mateo on 2007-04-01
> **ComplexNumber said:**
> what makes you think there is a program *and* an applet?

go to terminal and type 'tomboy'.  then right-click on your panel and go to Add to Panel.

---

### Post by Disstress on 2007-04-01
From what I understand you have to have the program installed in order to do anything with it, I am kind of lost. There is just a program, right?

---

### Post by ComplexNumber on 2007-04-01
> **Mateo said:**
> go to terminal and type 'tomboy'.  then right-click on your panel and go to Add to Panel.
just done that. what am i supposed to notice?

---

### Post by dbbolton on 2007-04-01
the panel "applet" is probably just a launcher/shortcut to the program.

---

### Post by Mateo on 2007-04-02
They are the same program, of course.  Just 2 separate ways of running it.  The applet is more of a frontend for Tomboy.  For one, when you click on the applet is gives a blue background.  This doesn't happen with the application.  Also, of course, like all applets the tomboy applet has to be removed from the panel, you don't simply close it.

---

### Post by ComplexNumber on 2007-04-02
> **dbbolton said:**
> the panel "applet" is probably just a launcher/shortcut to the program.
that's correct. tomboy, the applet, IS the program. is the same with gnome system monitor and every other program.

---

### Post by Mateo on 2007-04-02
it is the same program, of course.  it's a seperate way of running it.  my question always was, why have 2 seperate ways to do the exact same thing?

---

### Post by 23meg on 2007-04-02
For two separate use cases maybe? Not everyone using Tomboy is using gnome-panel, and thus can use panel applets.

---

### Post by Mateo on 2007-04-02
> **23meg said:**
> For two separate use cases maybe? Not everyone using Tomboy is using gnome-panel, and thus can use panel applets.

then why not just have the application?

the only advantage I see to the applet is that it can be placed anywhere, whereas the application runs in the Notification Area like all tray icons.

---

### Post by dbbolton on 2007-04-02
> **Mateo said:**
> then why not just have the application?

the only advantage I see to the applet is that it can be placed anywhere, whereas the application runs in the Notification Area like all tray icons.
no one is going to make you use the "applet" if you don't want to.

---

### Post by 23meg on 2007-04-02
> **Mateo said:**
> then why not just have the application?

the only advantage I see to the applet is that it can be placed anywhere, whereas the application runs in the Notification Area like all tray icons.

Another possible advantage is that it can be used regardless of the existence of a notification area. Not everyone who uses a panel must have one; yet another use case variation.

I don't know much about Mono and Tomboy's structure, but the development cost of having both an independent [1] "application" and a panel applet is almost certainly negligible.

[1] *Actually, there isn't one; the panel applet is the same /usr/lib/tomboy/Tomboy.exe that /usr/bin/tomboy points to, but called with a --panel-applet option*.

---

### Post by macogw on 2007-04-02
Having Tomboy in the notification area is a new thing.  That's in the newer version.  The one that was on Edgy did not go there, so you had to either go through the GNOME menus or use the one on the laucher or alt+f2 it

---

