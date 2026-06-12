---
title: "Does Compiz replace Gnome or KDE?"
date: 2006-05-31
forum: The Cafe
---

### Post by darrensnospam on 2006-05-31
Does Compiz replace Gnome and/or KDE?
(Yeah. Very basic question.):confused:

---

### Post by helpme on 2006-05-31
[QUOTE=darrensnospam]Does Compiz replace Gnome and/or KDE?
(Yeah. Very basic question.):confused:[/QUOTE]
No, it replaces the window managers they use, that is metacity and kwin.
However, afaik both metacity and kwin will take advantage of XGL/Aiglx in the future, so you won't need to run compiz to get at least some nice effects.

---

### Post by darrensnospam on 2006-05-31
helpme,

Thanks for your reply.

So in the future, I could run Gnome and I'd get some of the same effects at Compiz? Compiz is sort of an add on to Gnome for example?

Would in be more efficient running Gnome with XGL than running Compiz with Gnome? Or is that a non-issue?

-darrensnospam

---

### Post by Virogenesis on 2006-05-31
gnome is a DE (desktop envioment), a DE has a window manager.
Gnome's window manager is metacity, compiz can replace metacity within gnome.
The xgl is required by compiz.
XGL sits upon on a layer and provides a interface for the graphics card to talk basically giving you a faster desktop.

---

### Post by helpme on 2006-05-31
[QUOTE=darrensnospam]helpme,

Thanks for your reply.

So in the future, I could run Gnome and I'd get some of the same effects at Compiz? Compiz is sort of an add on to Gnome for example?

Would in be more efficient running Gnome with XGL than running Compiz with Gnome? Or is that a non-issue?

-darrensnospam[/QUOTE]
I think you have a few things mixed up here.
First off, Gnome is a desktop environment. As such it uses metacity as its default window manager. The only thing the window manager really does is, well, manage the windows. For example, it's responsible for drawing the window boarders and enabling you to move the windows.

Now that metacity is the default window manager does not mean that you can't run any other window manager with gnome. Just look around the forum here, there are for example a lot of people using openbox with gnome.

This is where compiz comes into play. Compiz is simply an other window manager that in addition to doing what a normal window manager does also takes advantages of the new possibilities that XGL offers, that is, it will also give you the nice effects.

At the moment people are working on enabling metacity to also take advantage of the new possibilities, so in the future you'll be able to use Gnome with its standard window manager and you'll also get some nice effects.

About what's being more efficient, I really don't know and I'll guess we'll have to wait and see. IIRC the guys behind compiz are of the opinion that it's easier to start a new window manager from scratch that takes advantage of the new possibilities rather then implementing this into an existing window manager. Of course, those working on metacity disagree.

Hope that cleared a few things up.

---

### Post by darrensnospam on 2006-05-31
Thanks, guys. This makes sense. I appreciate your clarification.

---

### Post by mrazster on 2006-05-31
Yeah..this was really useful info.....I also had it mixed up. But I think I got a little bit more hang of it.

---

### Post by s|k on 2006-05-31
Compiz is entirely broken for me. It doesn't replace anything!

---

### Post by Sammi on 2006-05-31
Hey what do you expect? It's still very new and in develpment, so isn't it unrealistic of you to think that it should work painlessly already?

And besides it works for me :mrgreen: hehehe

---

### Post by rado_london on 2006-05-31
[QUOTE=Sammi]Hey what do you expect? It's still very new and in develpment, so isn't it unrealistic of you to think that it should work painlessly already?

And besides it works for me :mrgreen: hehehe[/QUOTE]
You are so mean:neutral:

---

### Post by Sammi on 2006-05-31
I know :twisted: 

muah-hahaha... evil

---

### Post by ronlybonly on 2006-05-31
I just found out the difference between a DE and a window manager today and I've been using Linux off and on since Mandrakelinux 8.1 (or was it 8.0?) was released. :D
Can't wait to try out Xgl on Dapper tomorrow.

---

### Post by fuscia on 2006-05-31
what is xgl good for, other than making cubes out of everything?

---

### Post by mcduck on 2006-06-01
[QUOTE=fuscia]what is xgl good for, other than making cubes out of everything?[/QUOTE]
It makes your desktop more responsive, as drawing the screen is done with your GPU instead of CPU.

---

### Post by mostwanted on 2006-06-01
Drop shadows make the window stacking more apparent which is a plus for usability. Compiz also has an improved alt+tab functionality and can show all windows as thumbnails with the press of a button (the exposé effect from OSX).

---

